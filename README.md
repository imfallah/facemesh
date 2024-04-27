<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>
<h1 align="center">FACE MESH😎</h1>

<p align="center">
<img src="https://github.com/jokernets/facemesh/blob/main/images.jpeg">
</p>


### 🌏 Readme in [فارسی](https://github.com/jokernets/facemesh/blob/main/Fa.md)


<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>
<p align="center">
<img src="https://img.shields.io/badge/language-python-blue?style"/><img src="https://img.shields.io/github/stars/jokernets/audiotoplot"/><img src="https://img.shields.io/github/forks/jokernets/audiotoplot"/>
</p>

   


<h5 align="center">🛑Time to study 5 minutes⚠</h5>

Table of contents✅✔
=================

<!--ts-->
   * 🔸[Installation⚠](#installation)

   * 🔸[Anilayes Code📈](#analiys-code-)
     * 💫[Importing✔](#importing)
     * 💫[Set Variable✔](#set-variable)
     * 💫[Audio Input✔](#audio-input)
     * 💫[Define✔](#define)
     * 💫[Set Plot✔](#set-plot)
  
   * 🔸[Mor Example💯](#more-examples-and-showcase-)
     * 🥇[Project Video📺](#video-image-of-the-app-)
    
   * 🎁[`CONNECT ME🎃`](#connect-me)
<!--te-->

# Installation⚠

## Install the Library with pip:

```python
pip install opencv-python
pip install mediapipe
pip install tensorflow
pip install keras-models
```

Update existing installation:`pip3 install (YOUR LIBRARY) --upgrade`
(update as often as possible because this library is under active development)

# Analiys Code🎃:

## `Importing`♻🔰:
1.🔷 **Imported libraries**:

- `cv2`: OpenCV for image processing✅
      
-  `mediapipe`: a library for building multimodal perceptual models (eg, face, hand, gesture).✅
      
- `tensorflow.keras.models`: Keras models for machine learning.✅

2.🔷 **MediaPipe Face Mesh**:

- The solution code initializes the **MediaPipe Face Mesh** using the "mp_face_mesh" module.✅
- The Face Mesh solution is designed to detect and track facial features (such as eyes, nose, mouth, etc.) in real-time video streams or images.✅
- It can be used for various applications including facial feature analysis, augmented reality and facial expression recognition.✅

3.🔷 **Note**:
- The provided code snippet does not contain any specific functionality or usage beyond importing the necessary modules and initializing MediaPipe's Face Mesh solution.✅
- If you have specific tasks or requirements related to face mesh analysis, please provide additional context.✅
- Otherwise, the code fragment itself does not perform any special action.✅
```python
import cv2
import mediapipe as mp
from tensorflow.keras import models
mp_drawing = mp.solutions.drawing_utils
mp_drawing_styles = mp.solutions.drawing_styles
mp_face_mesh = mp.solutions.face_mesh

```
## `2`:
1.🔷 ** Setup and configuration **:
- The solution code initializes the **MediaPipe Face Mesh** with specific parameters:
- `static_image_mode=True`: indicates that the solution processes static images (not video streams).
- `max_num_faces=1`: specifies that only one face is detected (if there are multiple faces in the image).
- `refine_landmarks=True`: Enables the refinement of landmark positions.
- `min_detection_ confidence=0.5`: sets the minimum confidence threshold for face detection.

2.🔷 **Image processing**:
- For each image file in the "IMAGE_FILES" list:
- Read the image using OpenCV (`cv2.imread`).
- Convert BGR image to RGB format (`cv2.cvtColor(image, cv2.COLOR_BGR2RGB)`).
- Process the image using the Face Mesh solution ('face_mesh.process').
- If no specific facial features are detected, continue to the next image.
- Create an annotated copy of the image (`annotated_image`).
- Draw face mesh marks on the annotation image using different styles:
- `FACEMESH_TESSELATION`: Draws the mesh template.
- `FACEMESH_CONTOURS`: Draws the contours of the face.
- "FACEMESH_IRISES": Draws iris marks.
- Save the annotated image to a file (for example, `/tmp/annotated_image0.png`).

3. 🔷**Note**:
- The code snippet assumes that the "IMAGE_FILES" list contains valid image file paths.
- The Face Mesh solution detects facial features (such as eyes, nose, mouth, etc.) and depicts them on the image.
- Saved annotated images will show the facial features detected.
```python
# For static images:
IMAGE_FILES = []
drawing_spec = mp_drawing.DrawingSpec(thickness=1, circle_radius=1)
with mp_face_mesh.FaceMesh(
    static_image_mode=True,
    max_num_faces=1,
    refine_landmarks=True,
    min_detection_confidence=0.5) as face_mesh:
  for idx, file in enumerate(IMAGE_FILES):
    image = cv2.imread(file)
    # Convert the BGR image to RGB before processing.
    results = face_mesh.process(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    # Print and draw face mesh landmarks on the image.
    if not results.multi_face_landmarks:
      continue
    annotated_image = image.copy()
    for face_landmarks in results.multi_face_landmarks:
      print('face_landmarks:', face_landmarks)
      mp_drawing.draw_landmarks(
          image=annotated_image,
          landmark_list=face_landmarks,
          connections=mp_face_mesh.FACEMESH_TESSELATION,
          landmark_drawing_spec=None,
          connection_drawing_spec=mp_drawing_styles
          .get_default_face_mesh_tesselation_style())
      mp_drawing.draw_landmarks(
          image=annotated_image,
          landmark_list=face_landmarks,
          connections=mp_face_mesh.FACEMESH_CONTOURS,
          landmark_drawing_spec=None,
          connection_drawing_spec=mp_drawing_styles
          .get_default_face_mesh_contours_style())
      mp_drawing.draw_landmarks(
          image=annotated_image,
          landmark_list=face_landmarks,
          connections=mp_face_mesh.FACEMESH_IRISES,
          landmark_drawing_spec=None,
          connection_drawing_spec=mp_drawing_styles
          .get_default_face_mesh_iris_connections_style())
    cv2.imwrite('/tmp/annotated_image' + str(idx) + '.png', annotated_image)
```
## `3` :
1. 🔷**initial setting**:
- The "cap" variable is created using "cv2.VideoCapture(0)".
- "cv2.VideoCapture(0)" starts the webcam to capture video frames.
- The "0" argument indicates that the default camera (usually the built-in webcam) should be used.
2.🔷**design specifications**:
- The 'drawing_spec' variable is created with certain parameters:
- `thickness=1`: sets the thickness of the lines used to draw symbols.
- `circle_radius=1`: Sets the radius of the circles used to draw symbols.
3.🔷 **Note**:
- The code assumes that a webcam is available and accessible.
- The webcam captures video frames that can be processed using a Face Mesh solution or other computer vision techniques.
```python
# For webcam input:
drawing_spec = mp_drawing.DrawingSpec(thickness=1, circle_radius=1)
cap = cv2.VideoCapture(0)
```
## `4` :  

1. 🔷** Setup and configuration **:
- The solution code initializes the **MediaPipe Face Mesh** with specific parameters:
- `max_num_faces=1`: specifies that only one face is detected (if there are multiple faces in the frame).
- `refine_landmarks=True`: Enables the refinement of landmark positions.
- `min_detection_spection=0.5`: sets the minimum confidence threshold for face detection.
- `min_tracking_ confidence=0.5`: sets the minimum confidence threshold for face tracking.

2. 🔷**Processing video frames**:
- The code enters a loop that takes video frames from the camera (webcam) using `cap.read()`.
- If a frame is not successfully read, it prints "Ignoring empty camera frame" and continues to the next frame.
- The image is converted from BGR format to RGB format (`cv2.cvtColor(image, cv2.COLOR_BGR2RGB)`).
- The Face Mesh solution processes the image using "face_mesh.process(image)".
- If face landmarks are detected (`results.multi_face_landmarks`), the landmarks are drawn on the image using different styles:
- `FACEMESH_TESSELATION`: Draws the mesh template.
- `FACEMESH_CONTOURS`: Draws the contours of the face.
- "FACEMESH_IRISES": Draws iris marks.
  - The image is flipped horizontally to display the selfie (`cv2.flip(image, 1)`).
  - The processed frame is displayed in a window called "MediaPipe Face Mesh".
  - This loop continues until pressing the Esc key (key code 27).

3.🔷 **Note**:
- The code assumes that a camera (webcam) is available and accessible.
- Face Mesh solution detects facial landmarks and visualizes them on video frames.
- User can close the window by pressing 'Esc' key.
- The code snippet does not handle exceptions related to camera access or video frame reading.
```python
with mp_face_mesh.FaceMesh(
    max_num_faces=1,
    refine_landmarks=True,
    min_detection_confidence=0.5,
    min_tracking_confidence=0.5) as face_mesh:
  while cap.isOpened():
    success, image = cap.read()
    if not success:
      print("Ignoring empty camera frame.")
      # If loading a video, use 'break' instead of 'continue'.
      continue

    # To improve performance, optionally mark the image as not writeable to
    # pass by reference.
    image.flags.writeable = False
    image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
    results = face_mesh.process(image)

    # Draw the face mesh annotations on the image.
    image.flags.writeable = True
    image = cv2.cvtColor(image, cv2.COLOR_RGB2BGR)
    if results.multi_face_landmarks:
      for face_landmarks in results.multi_face_landmarks:
        mp_drawing.draw_landmarks(
            image=image,
            landmark_list=face_landmarks,
            connections=mp_face_mesh.FACEMESH_TESSELATION,
            landmark_drawing_spec=None,
            connection_drawing_spec=mp_drawing_styles
            .get_default_face_mesh_tesselation_style())
        mp_drawing.draw_landmarks(
            image=image,
            landmark_list=face_landmarks,
            connections=mp_face_mesh.FACEMESH_CONTOURS,
            landmark_drawing_spec=None,
            connection_drawing_spec=mp_drawing_styles
            .get_default_face_mesh_contours_style())
        mp_drawing.draw_landmarks(
            image=image,
            landmark_list=face_landmarks,
            connections=mp_face_mesh.FACEMESH_IRISES,
            landmark_drawing_spec=None,
            connection_drawing_spec=mp_drawing_styles
            .get_default_face_mesh_iris_connections_style())
    # Flip the image horizontally for a selfie-view display.
    cv2.imshow('MediaPipe Face Mesh', cv2.flip(image, 1))
    if cv2.waitKey(5) & 0xFF == 27:
      break
```
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>



## More Examples and Showcase 👑

### Video image of the APP 📺


# `𝐂𝐨𝐧𝐧𝐞𝐜𝐭 𝐌𝐞`🎈🎃

<a herf="https://www.buymeacoffee.com/jokernets"><img src="https://cdn.buymeacoffee.com/buttons/v2/arial-yellow.png" alt="Buy Me A Coffee" width="180px">
<a href="mailto:joker.until33@gmail.com"><img align="center" width="60px" src="https://github.com/edent/SuperTinyIcons/raw/master/images/svg/gmail.svg" style="max-width: 100%;"></a><a href="https://www.linkedin.com/" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="https://www.linkedin.com/in/mohammadfallahnejad/" height="40" width="60" /></a>
