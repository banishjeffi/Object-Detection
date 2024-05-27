# Object-Detection
## 💫 About Developer:

### Banish J

🤖 AI & ML Developer | Data Science & Analytics Expert  
🌐 Web Apps & IoT Skilled | Awesome UI Creator  
💻 AI is my main focus! 👾

## 📞 Contact
##### **☎️**   [9444333914](tel:9444333914)
##### **📧**  [mail@banish.in](mailto:mail@banish.in)
##### **🌐**  [Banish](https://www.banish.in)

## Core Concept

***This script continuously captures video from the webcam, performs object detection on each frame using the MobileNet SSD model, and displays the results in real-time. It exits when the 'q' key is pressed and provides FPS information at the end.windows.***

### Importing Necessary Libraries
```python
import numpy as np
import imutils
from imutils.video import FPS
import cv2
import time
```
- **numpy**: For numerical operations.
- **imutils**: A convenient library for basic image processing functions.
- **imutils.video**: Provides video processing utilities.
- **cv2**: The OpenCV library for computer vision tasks.
- **time**: A module to handle time-related tasks.

### Setting Up Model and Parameters
```python
prototxt = "MobileNetSSD_deploy.prototxt.txt"
model = "MobileNetSSD_deploy.caffemodel"
confThresh = 0.2
```
- **prototxt**: Path to the prototxt file containing the model architecture.
- **model**: Path to the pre-trained caffemodel file containing the learned weights.
- **confThresh**: Confidence threshold for object detection.

### Class Labels and Colors
```python
CLASSES = ["background", "aeroplane", "bicycle", "bird", "boat",
    "bottle", "bus", "car", "cat", "chair", "cow", "diningtable",
    "dog", "horse", "motorbike", "person", "pottedplant", "sheep",
    "sofa", "train", "tvmonitor"]
COLORS = np.random.uniform(0, 255, size=(len(CLASSES), 3))
```
- **CLASSES**: List of class labels for objects the model can detect.
- **COLORS**: Randomly generated colors for each class label.

### Loading Model
```python
net = cv2.dnn.readNetFromCaffe(prototxt, model)
```
- **cv2.dnn.readNetFromCaffe**: Loads the pre-trained model from the prototxt and caffemodel files.

### Initializing Video Stream
```python
vs = cv2.VideoCapture(0)
time.sleep(2.0)
```
- **cv2.VideoCapture(0)**: Initializes the webcam for video capture. The argument `0` typically refers to the default webcam on the computer.
- **time.sleep(2.0)**: Introduces a delay of 2 seconds to allow the webcam to warm up.

### Initializing FPS Counter
```python
fps = FPS().start()
```
- **FPS()**: Initializes the FPS counter.

### Real-Time Object Detection Loop
```python
while True:
    _, frame = vs.read()
    frame = imutils.resize(frame, width=1000)

    # Blob preprocessing...
    # Forward pass through the network...
    # Object detection and drawing...
```
- **vs.read()**: Captures a frame from the webcam.
- **imutils.resize**: Resizes the frame to have a maximum width of 1000 pixels.

### Object Detection and Drawing
- The code performs object detection using the MobileNet SSD model on each frame captured from the webcam.
- Detected objects are drawn on the frame with bounding boxes and class labels.

### Exiting the Loop
```python
if key == ord("q"):
    break
```
- The loop exits if the 'q' key is pressed.

### Cleanup
```python
fps.stop()
vs.release()
cv2.destroyAllWindows()
```
- **fps.stop()**: Stops the FPS counter and displays the elapsed time and average FPS.
- **vs.release()**: Releases the webcam resource.
- **cv2.destroyAllWindows()**: Closes all OpenCV windows.
