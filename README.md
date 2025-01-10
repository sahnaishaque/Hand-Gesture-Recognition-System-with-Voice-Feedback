# Hand Gesture Recognition System with Voice Feedback

## Overview
This project implements a real-time hand gesture recognition system using computer vision and machine learning techniques. It features voice feedback for detected gestures, making it accessible and user-friendly. The system uses OpenCV for image processing, MediaPipe for hand tracking, and pyttsx3 for voice synthesis.

## Features
- Real-time hand gesture recognition
- Voice feedback for detected gestures
- Support for multiple hand gestures
- Gesture history tracking
- FPS display
- Training mode for new gestures
- Performance optimized with threaded voice processing

## Prerequisites
- Python 3.7 or higher
- Webcam or USB camera
- Operating System: Windows, macOS, or Linux

## Required Dependencies
```bash
pip install opencv-python
pip install mediapipe
pip install numpy
pip install pyttsx3
```

## Project Structure
```
gesture-recognition/
│
├── main.py                # Main application file
├── model/                 # Model-related files
│   ├── keypoint_classifier/
│   │   ├── keypoint.csv
│   │   ├── keypoint_classifier.py
│   │   └── keypoint_classifier_label.csv
│   └── point_history_classifier/
│       ├── point_history.csv
│       ├── point_history_classifier.py
│       └── point_history_classifier_label.csv
├── utils/
│   └── cvfpscalc.py      # FPS calculation utility
└── README.md             # This file
```

## Installation
1. Clone the repository:
```bash
git clone <repository-url>
cd gesture-recognition
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Ensure your webcam is connected and functioning properly.

## Usage

### Running the Application
1. Start the program:
```bash
python main.py
```

2. Optional command-line arguments:
```bash
python main.py --device 0 --width 960 --height 540
```

### Command Line Arguments
- `--device`: Camera device number (default: 0)
- `--width`: Camera capture width (default: 960)
- `--height`: Camera capture height (default: 540)
- `--use_static_image_mode`: Enable static image mode
- `--min_detection_confidence`: Minimum confidence for detection (default: 0.7)
- `--min_tracking_confidence`: Minimum confidence for tracking (default: 0.5)

### Key Controls
- `ESC`: Exit the program
- `k`: Enter keyboard mode for gesture registration
- `h`: Enter history mode
- `c`: Capture current gesture for training

## Gesture Recognition Modes

### 1. Normal Mode
- Default mode for gesture recognition
- Displays recognized gestures with voice feedback
- Shows bounding box and hand landmarks

### 2. Keyboard Mode (Training Mode)
- Press 'k' to enter this mode
- Used for registering new gestures
- Each gesture is assigned an incremental ID
- Follow on-screen instructions for registration

### 3. History Mode
- Press 'h' to enter this mode
- Tracks gesture movement history
- Useful for dynamic gesture recognition

## Voice Feedback System
The system provides voice feedback for recognized gestures with the following features:

- Clean voice output (just the gesture name)
- Gesture stability checking to prevent flickering
- Configurable cooldown between announcements
- Threading to prevent performance impact

### Voice Settings
You can adjust these parameters in the code:
```python
SPEAK_COOLDOWN = 0.5        # Time between announcements
STABILITY_THRESHOLD = 3      # Frames needed for stable gesture
voice_engine.setProperty('rate', 150)    # Speaking rate
voice_engine.setProperty('volume', 0.9)   # Volume level
```

## Customizing Gestures
1. Enter keyboard mode (press 'k')
2. Press 'c' to capture the gesture
3. Perform the gesture and hold
4. Add the gesture label to `model/keypoint_classifier/keypoint_classifier_label.csv`

## Troubleshooting

### Common Issues
1. Camera not detected:
   - Check if the camera is properly connected
   - Try different values for --device argument

2. Voice not working:
   - Ensure pyttsx3 is properly installed
   - Check system sound settings
   - Try reinstalling pyttsx3: `pip uninstall pyttsx3 && pip install pyttsx3`

3. Poor recognition:
   - Ensure good lighting conditions
   - Keep hands within camera frame
   - Adjust min_detection_confidence and min_tracking_confidence

### Performance Optimization
- Reduce camera resolution for better performance
- Adjust SPEAK_COOLDOWN for smoother voice feedback
- Consider reducing STABILITY_THRESHOLD if gesture detection feels slow

## Contributing
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Acknowledgments
- MediaPipe for hand tracking
- OpenCV team for computer vision tools
- pyttsx3 developers for text-to-speech functionality

## Future Improvements
- [ ] Add support for custom voice profiles
- [ ] Implement gesture combination recognition
- [ ] Add GUI for gesture training
- [ ] Improve gesture stability algorithm
- [ ] Add support for more languages