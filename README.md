# AI-Based Intelligent Driving Assistance System Using Edge AI

A research prototype exploring AI-assisted driving, obstacle
avoidance, and edge computing using a wheeled robot.

## Overview

The system allows an operator to control a small robot while
a LiDAR-based safety layer blocks movement toward nearby obstacles.

A camera-based deep learning model classifies road users into
six categories. Integrating this perception module with the
existing safety system remains future work.

## Hardware

- NVIDIA Jetson Orin Nano Super Developer Kit
- RPLIDAR A1 laser scanner
- Logitech USB webcam
- L298N motor driver
- Two DC gear motors
- DualShock 4 controller
- Wheeled robot chassis

## Technologies

- Python
- TensorFlow / Keras
- MobileNetV2
- OpenCV
- NumPy
- LiDAR-based obstacle sensing
- NVIDIA Jetson platform

## Vehicle Classification

The MobileNetV2-based model classifies images into six classes:

1. Auto Rickshaws
2. Bikes
3. Cars
4. Motorcycles
5. Human
6. Unknown

The notebook reports approximately 99.37% validation accuracy
after fine-tuning. This is a validation result, not a guarantee
of real-world accuracy.

## Obstacle Safety Logic

The prototype uses front and rear LiDAR protection sectors.

- Below 500 mm: the corresponding direction is blocked.
- Above 700 mm: the direction is released.
- Between 500 mm and 700 mm: the previous state is maintained.

This hysteresis helps prevent rapid stop-start switching near
the distance thresholds.

These are prototype settings, not certified safe stopping distances.

## Current Status

| Component | Status |
|---|---|
| LiDAR communication | Verified in the reported prototype |
| GPIO motor direction control | Verified in the reported prototype |
| Controller input handling | Verified in the reported prototype |
| LiDAR stopping logic | Implemented |
| Camera classification | Demonstrated on sample scenes |
| Held-out model evaluation | Pending |
| Classifier deployment on Jetson | Pending |
| Classifier integration with motor safety logic | Pending |
| Stopping-distance and latency measurements | Pending |

## Future Work

- Evaluate the model on an independent test dataset.
- Generate a confusion matrix and classification report.
- Deploy the classifier on the Jetson with the chassis camera.
- Measure inference latency and frames per second.
- Investigate PWM speed control and wheel encoders.
- Explore camera and LiDAR sensor fusion.
- Test safety behaviour under different conditions.

## Safety Disclaimer

This is a research prototype, not a certified automotive
driver-assistance system. The camera classifier is not currently
connected to the motor safety layer.

## Authors

Vijay Wankhede, Rajat Bhati, Ujjwal Singh

Department of Electronics and Electrical Engineering  
MIT World Peace University, Pune, India
