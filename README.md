#### Tracking-Device-Using-Raspberry-Pi-and-Raspberry-Pi-Cam:

This project involves creating a face-tracking device using a Raspberry Pi, Picamera2, OpenCV, and servo motors. 
The device uses a camera to capture video frames and detect faces in real-time. 
Based on the detected face's position, it adjusts the angles of two servo motors to keep the face centered in the frame.

#### Initialisation:

>GPIO Setup: Configures GPIO pins for controlling the servo motors.
Servo Initialization: Initializes the PWM signals for two servos controlling horizontal and vertical movements.
Camera Initialization: Starts the Picamera2 to capture video frames.
Haar Cascade Classifier: Loads a pre-trained Haar Cascade classifier (haarcascade_frontalface_default.xml) for face detection.

>Servo Control Functions:
map_servo_position: Maps face position to servo angles.
low_pass_filter: Smoothens target positions for stable servo movement.
set_servo_position: Moves servos to target positions smoothly.

>Main Loop:
Captures video frames.
Converts frames to grayscale.
Detects faces using the Haar Cascade classifier.
Calculates the center of the detected face and maps it to servo positions.
Smoothly adjusts servos to keep the face centered.
Displays the video frame with a rectangle around the detected face.
Exits on 'q' key press.

>Cleanup: Stops the camera, closes OpenCV windows, stops PWM, and cleans up GPIO settings.

#### Usage of Haar Cascade File 
The haarcascade_frontalface_default.xml file is crucial for the face detection component of this project.
It is a pre-trained model that identifies faces in the video frames. 

>Loading the Classifier: The file is loaded into OpenCV using cv2.CascadeClassifier, creating a classifier object that can detect faces.
Python code: face_cascade = cv2.CascadeClassifier(cascade_path)
>Face Detection: The classifier's detectMultiScale method is used to find faces in each grayscale frame. This method returns the coordinates and sizes of any detected faces.
Python code: faces = face_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=5, minSize=(30, 30))
>Processing Detected Faces: The detected face's position is used to calculate servo positions, ensuring the camera tracks and centers on the face.
