# Safe Pick and Place Operation of Yaskawa Robot

This project utilizes an ultrasonic distance sensor to measure the distance of objects and ensures safe pick-and-place operations for a Yaskawa robot. The code reads distance data in real time and displays it on an LCD screen, providing feedback to the operator about object placement accuracy. It also prints the data to the serial monitor for debugging and monitoring purposes.

---

## How It Works

### **1. Ultrasonic Distance Sensor**
- **Pins Used:**
  - `trigPin`: Pin 8, used to send a trigger pulse to the ultrasonic sensor.
  - `echoPin`: Pin 7, used to receive the echo pulse from the ultrasonic sensor.
  
- **Measurement Process:**
  - The sensor sends an ultrasonic pulse using the `trigPin`.
  - The time taken for the pulse to return to the `echoPin` is measured using `pulseIn()`.
  - Distance is calculated using the formula:
    ```
    Distance = (Speed of Sound * Time) / 2
    ```
    - **Speed of Sound**: 0.0347 cm/µs.

### **2. LCD Display**
- A 16x2 I2C LCD module is used to display the measured distance:
  - **First Line:** Displays the distance in centimeters (e.g., "50 cms").
  - **Second Line:** Displays the distance in inches (e.g., "19.68 inches").

### **3. Serial Monitor Feedback**
- The distance in both centimeters and inches is printed to the serial monitor for real-time debugging and analysis:
- Distance: 50cms --- 19.68inches


---

## Features
1. **Real-Time Distance Measurement:**
 - Measures the distance of objects using an ultrasonic sensor.
 
2. **Dual Output:**
 - Displays distance in both centimeters and inches.

3. **LCD Feedback:**
 - Provides visual feedback on the measured distance.

4. **Serial Monitor Output:**
 - Prints detailed distance information for monitoring.

---

## Components Required
1. **Ultrasonic Sensor (e.g., HC-SR04):**
 - Sends ultrasonic waves and receives reflected waves to measure distance.

2. **16x2 I2C LCD Display:**
 - Displays the measured distance in real-time.

3. **Arduino Board:**
 - Executes the code and interfaces with the components.

4. **Yaskawa Robot (Optional):**
 - Uses the distance data for safe pick-and-place operations.

---

## Code Walkthrough

### **1. Variable Definitions**
- `trigPin` and `echoPin`: Define the pins for the ultrasonic sensor.
- `speed`: Speed of sound in cm/µs.
- `dist`: Distance in centimeters.
- `pingTime`: Time taken for the echo pulse.
- `distinch`: Distance in inches.

### **2. `setup()` Function**
- Initializes serial communication (`Serial.begin(9600)`).
- Configures `trigPin` as an output and `echoPin` as an input.
- Initializes the LCD:
- Displays a startup message:  
  ```
  CIRCUITSCHOOLS..
  Distance sensor
  ```

### **3. `loop()` Function**
- **Triggering the Sensor:**
- Sends a 10 µs HIGH pulse to the `trigPin` to initiate the ultrasonic signal.

- **Measuring Echo Time:**
- The `pulseIn()` function records the time for the echo signal to return to the sensor.

- **Calculating Distance:**
- Distance in centimeters:
  ```
  dist = (speed * pingTime * 0.5);
  ```
- Distance in inches:
  ```
  distinch = dist / 2.54;
  ```

- **Output:**
- Prints the calculated distance to the serial monitor.
- Displays the distance in both centimeters and inches on the LCD.

- **Delay:**
- Adds a delay of 250 ms to ensure stable readings.

---

## Example Output

### **Serial Monitor:**
- Distance: 50cms --- 19.68inches Distance: 45cms --- 17.72inches


### **LCD Display:**
- 50cms 19.68inch


---

## Applications
- **Safe Pick-and-Place Operations:**
  - Ensures accurate object placement for a Yaskawa robot by verifying object distance.

- **Obstacle Detection:**
  - Can be extended for use in robotics for obstacle avoidance.

- **Educational Purposes:**
  - Demonstrates real-time distance measurement and Arduino-LCD interfacing.

---

## Future Enhancements
1. Integrate the sensor data directly with the Yaskawa robot's control system.
2. Implement thresholds for distance to trigger automatic pick-and-place actions.
3. Add a warning system (e.g., buzzer) for out-of-range distances.




