# Ball and Beam Control System - README

## Overview
This project models and controls a ball and beam system using Simscape Multibody in MATLAB. The system consists of a ball rolling on a beam, which is tilted by a servo motor through a lever arm. The goal is to control the ball's position on the beam using a lead compensator controller, ensuring the system meets specific design criteria: settling time less than 3 seconds and overshoot less than 5%.


---

## System Description
The physical system consists of the following components:
1. **Ball**: Rolls along the beam without slipping. Its motion is influenced by gravity and the beam's angle.
2. **Beam**: Tilted by a lever arm connected to a servo motor. The beam's angle determines the ball's acceleration.
3. **Servo Motor**: Controls the beam's angle by rotating a gear, which moves the lever arm.
4. **Lever Arm**: Connects the servo gear to the beam, translating the gear's rotation into beam tilt.

---

## Key Parameters
| Symbol | Description                     | Value/Unit          |
|--------|---------------------------------|---------------------|
| m      | Mass of the ball                | 0.11 kg             |
| R      | Radius of the ball              | 0.015 m             |
| d      | Lever arm offset                | 0.03 m              |
| g      | Gravitational acceleration      | 9.8 m/s²            |
| L      | Length of the beam              | 1.0 m               |
| J      | Ball's moment of inertia        | 9.99e-6 kg·m²       |
| r      | Ball position coordinate        | Variable            |
| α      | Beam angle coordinate           | Variable            |
| θ      | Servo gear angle                | Variable            |

---

## Modeling Steps
1. **Physical Setup**:
   - Define the system's physical components (ball, beam, lever, gear) and their properties.
   - Ensure the ball rolls without slipping and friction is negligible.

2. **Simscape Multibody Model**:
   - Create a Simscape Multibody model to simulate the system.
   - Configure gravity, solver settings, and joint constraints.

3. **Gear and Lever Assembly**:
   - Model the servo gear and lever arm to translate rotational motion into beam tilt.
   - Add pins and joints to represent physical connections.

4. **Beam and Ball Constraints**:
   - Define the beam's motion and its connection to the lever.
   - Add constraints to ensure the ball rolls along the beam without slipping.

5. **Controller Implementation**:
   - Design a lead compensator to control the ball's position.
   - Close the loop by feeding the ball's position back to the controller.

---

## Simulation Results
- The system achieves the desired performance:
  - Settling time: Less than 3 seconds.
  - Overshoot: Less than 5%.
- The ball's position is controlled accurately, and the system responds smoothly to step inputs.

---

## Files and Instructions
1. **Model Files**:
   - `ball_beam_model.slx`: Simulink model of the ball and beam system.
   - `ball_beam_properties.m`: MATLAB script to define system parameters.

2. **Running the Simulation**:
   - Open the Simulink model (`ball_beam_model.slx`).
   - Run the `ball_beam_properties.m` script to load parameters.
   - Simulate the model and observe the results on the Scope.

3. **Controller Tuning**:
   - Adjust the lead compensator parameters in the `Lead Compensator` block if necessary.
   - Modify the gain values to optimize system performance.

---

## Dependencies
- MATLAB R2019b or later.
- Simscape Multibody toolbox.

---

## Notes
- Ensure the solver settings are configured as follows:
  - Solver type: `ode23t`.
  - Absolute tolerance: `1e-4`.
- The model assumes no slipping and negligible friction. Adjust parameters if real-world conditions differ.

---

## License
This project is open-source and available under the MIT License. Feel free to modify and distribute it as needed.

---

For questions or feedback, please contact the project maintainer.
