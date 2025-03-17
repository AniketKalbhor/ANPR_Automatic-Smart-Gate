# Automatic Smart Gate Surveillance System

## Project Overview
The Automatic Smart Gate Surveillance System is an intelligent security solution that automates vehicle access control using computer vision and IoT technologies. The system captures images of vehicle license plates, processes them using OpenCV and OCR, validates them against an authorized database, and controls gate operations accordingly.

## Features
- Real-time license plate detection and recognition
- Database integration for authorized vehicle validation
- Automated gate control system
- Mobile app for administrator control
- Real-time monitoring through ThingSpeak IoT platform

## Technical Stack

### Hardware Components
- NodeMCU ESP8266 microcontroller
- Camera module for image capture
- Servo motor for gate control
- IR sensors for vehicle detection (optional)

### Software Technologies
- **OpenCV**: For image processing and contour detection
- **EasyOCR**: For optical character recognition of license plates
- **Python**: Primary programming language
- **Google Colab**: For model development and testing
- **Firebase RTDB**: NoSQL database for storing authorized vehicles
- **ThingSpeak**: IoT platform for communication between detection system and gate controller
- **Matplotlib**: For visualization during development
- **NumPy**: For numerical operations on images
- **Imutils**: For image processing utilities

## System Architecture
The system follows a modular architecture:
1. **Image Acquisition Module**: Captures vehicle images using a camera
2. **License Plate Detection Module**: Processes images to locate and extract license plates using OpenCV
3. **Character Recognition Module**: Converts license plate images to text using EasyOCR
4. **Database Validation Module**: Compares extracted license numbers with authorized database
5. **Gate Control Module**: Manages gate operations based on validation results via ThingSpeak and NodeMCU

## Algorithm Flow
1. **Image Preprocessing**:
   - Convert image to grayscale
   - Apply bilateral filter for noise reduction
   - Use Canny edge detection for edge identification

2. **License Plate Localization**:
   - Find contours in the processed image
   - Sort contours by area
   - Identify quadrilateral shapes that could be license plates

3. **License Plate Extraction**:
   - Create a mask using the identified license plate region
   - Extract the license plate region from the original image

4. **Character Recognition**:
   - Use EasyOCR to read text from the extracted license plate
   - Format the text by removing spaces and converting to uppercase

5. **Database Validation**:
   - Compare the extracted license number with the authorized database
   - Determine access permission based on the comparison result

6. **Gate Control**:
   - Send gate control commands to ThingSpeak based on validation results
   - NodeMCU reads ThingSpeak field values and controls the gate accordingly

## Performance Metrics
- License plate detection accuracy: ~75%
- System response time: Real-time
- Gate operation lag: Minimal (< 1 second)

## Firebase Database Structure
- NoSQL format with key-value pairs
- Key: Flat number
- Value: Associated vehicle license number

## ThingSpeak Integration
- API Key: UMG764PWG2V56RJ7
- Field1: Gate status (0 = Closed, 1 = Open)
- Real-time status monitoring and historical data visualization

## Installation and Setup

### Prerequisites
- Python 3.7+
- OpenCV
- EasyOCR
- NumPy
- Matplotlib
- Imutils
- Firebase account
- ThingSpeak account
- NodeMCU with necessary libraries

### Installation Steps
```python
# Install required Python packages
pip install opencv-python
pip install easyocr
pip install numpy
pip install matplotlib
pip install imutils
pip install firebase-admin
pip install urllib3
```

### Hardware Setup
1. Connect NodeMCU to gate motor mechanism
2. Position camera with clear view of approaching vehicles
3. Ensure stable internet connection for ThingSpeak communication

## Usage
1. Power on the system
2. The camera automatically captures images of approaching vehicles
3. The system processes the image and extracts the license plate number
4. The system validates the license plate against the authorized database
5. If authorized, the gate opens automatically
6. If unauthorized, the driver proceeds with manual verification by security personnel

## Future Enhancements
- Implement machine learning for improved license plate detection accuracy
- Add facial recognition for additional security layer
- Develop a more sophisticated mobile app with real-time notifications
- Integrate with other security systems like CCTV

## Limitations and Challenges
- Performance may vary in different lighting conditions
- Accuracy depends on the quality of license plate images
- Requires stable internet connection for IoT communication
- Current prototype accuracy is around 75%
