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
     * 🥇[Importing](#importing)
     * 🥇[VideoCapture](#set-variable)
     * 🥇[Define](#audio-input)
     * 🥇[Run it !](#set-plot)

       * 🤍[HOW TO USE](#how-to-use-) 
  
   * 🔸[Mor Example💯](#more-examples-and-showcase-)
     * 🥇[Project Video📺](#video-image-of-the-app-)
     * 
   * 🎁[`CONNECT ME🎃`](#connect-me)
<!--te-->

# Installation⚠

## Install the Library with pip:

```python
pip install opencv-python
pip install mediapipe
```
Update existing installation:`pip3 install (YOUR LIBRARY) --upgrade`
(update as often as possible because this library is under active development)

# Analiys Code🎃:

## `Importing`♻🔰:

```python
import cv2
import mediapipe as mp
```
## `VideoCapture`:
1️⃣`cam = cv2.VideoCapture(0)`: This line enables the webcam. The number 0 means the first camera connected to the system.

2️⃣`width = int(cam.get(cv2.CAP_PROP_FRAME_WTH))` and `height = int(cam.get(cv2.CAP_PROP_FRAME_HEIGHT))`: These two linescapture the frames of the video.

3️⃣`cam.set(cv2.CAP_PROP_FPS, 30)`: This line sets the number of frames per second (FPS) to 30.

4️⃣`cam.set(cv2.CAP_PROP_FOURCC, cv2.VideoWriter_fourcc(*'MJPG'))`: This line sets the video codec to MJPG.

`faceMesh = mp.solutions.face_mesh.FaceMesh(False,1,True,0.5,0.5)`: This line creates a face mesh that is used to detect face keys.

5️⃣`mpDraw = mp.solutions.drawing_utils`: This tool draws the line used to draw the key points of the face on the video frames.

6️⃣`drawSpecCircle = mpDraw.DrawingSpec(thickness=1, circle_radius = 1, color=(0,255,0))` and `drawSpecLine = mpDraw.DrawingSpec(thickness=1, circle_radius = 1, color=(255,0,0 ))`: These two specification lines draw points and lines. Color is defined as RGB. Here, the dots will be green and the lines will be red.
```python
cam = cv2.VideoCapture(0)
width = int(cam.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cam.get(cv2.CAP_PROP_FRAME_HEIGHT))
#print(width,height)
cam.set(cv2.CAP_PROP_FPS, 30)
cam.set(cv2.CAP_PROP_FOURCC, cv2.VideoWriter_fourcc(*'MJPG'))
faceMesh = mp.solutions.face_mesh.FaceMesh(False,1,True,0.5,0.5)
mpDraw = mp.solutions.drawing_utils
drawSpecCircle = mpDraw.DrawingSpec(thickness=1,circle_radius = 1, color=(0,255,0))
drawSpecLine = mpDraw.DrawingSpec(thickness=1,circle_radius = 1,color=(255,0,0))
```
## `Define`🔧⚒️:
- `_, frame = cam.read()`: This line reads a frame from the video.
- `frameRGB = cv2.cvtColor(frame,cv2.COLOR_BGR2RGB)`: This line changes the color of the frame from BGR to RGB. This change is necessary because OpenCV reads frames in BGR format, but Mediapipe requires RGB format.
- `results = faceMesh.process(frameRGB)`: This line passes the frame to the face detection model and receives the results.
- `if results.multi_face_landmarks != None`: This line checks if a face is detected in the frame.
- `for faceLandmarks in results.multi_face_landmarks`: This loop is executed for each detected face in the frame.
- `connections= mp.solutions.face_mesh_connections.FACEMESH_...`: These lines define connection points between face keypoints.
- `mpDraw.draw_landmarks(frame,faceLandmarks,connections,drawSpecCircle,drawSpecLine)`: This line draws key points and connection lines on the frame.
- `cv2.imshow('jokernets', frame)`: This line displays the frame.
- `if cv2.waitKey(1) & 0xff == ord('q')`: This line checks if the user has pressed the 'q' key or not. If the user presses the 'q' key, the loop ends and the program ends.
```python
while True:
    _, frame = cam.read()
    frameRGB = cv2.cvtColor(frame,cv2.COLOR_BGR2RGB)
    results = faceMesh.process(frameRGB)
    if results.multi_face_landmarks != None:
        for faceLandmarks in results.multi_face_landmarks:
            connections= mp.solutions.face_mesh_connections.FACEMESH_LIPS
            connections= mp.solutions.face_mesh_connections.FACEMESH_LEFT_EYE
            connections= mp.solutions.face_mesh_connections.FACEMESH_LEFT_IRIS
            connections= mp.solutions.face_mesh_connections.FACEMESH_LEFT_EYEBROW
            connections= mp.solutions.face_mesh_connections.FACEMESH_RIGHT_EYE
            connections= mp.solutions.face_mesh_connections.FACEMESH_RIGHT_IRIS
            connections= mp.solutions.face_mesh_connections.FACEMESH_RIGHT_EYEBROW
            connections= mp.solutions.face_mesh_connections.FACEMESH_FACE_OVAL
            connections= mp.solutions.face_mesh_connections.FACEMESH_TESSELATION
            mpDraw.draw_landmarks(frame,faceLandmarks,connections,drawSpecCircle,drawSpecLine)
    cv2.imshow('jokernets', frame)
    if cv2.waitKey(1) & 0xff == ord('q'):
        print('end')
        break
```
## `Run!` :  
➖`cam.release()`: This line releases the camera. After the camera is released, it can no longer be used to read video frames.
➖ `cv2.destroyAllWindows()`: This line closes all windows opened by OpenCV. If no window is open, this line has no effect.
### HOW TO USE :
- run `main.py` without any [requirments](https://github.com/jokernets/facemesh/requirments.md)

```python
cam.release()
cv2.destroyAllWindows()
```
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>




## More Examples and Showcase 👑

### Video image of the APP 📺


# `𝐂𝐨𝐧𝐧𝐞𝐜𝐭 𝐌𝐞`🎈🎃

<a herf="https://www.buymeacoffee.com/jokernets"><img src="https://cdn.buymeacoffee.com/buttons/v2/arial-yellow.png" alt="Buy Me A Coffee" width="180px">
<a href="mailto:joker.until33@gmail.com"><img align="center" width="60px" src="https://github.com/edent/SuperTinyIcons/raw/master/images/svg/gmail.svg" style="max-width: 100%;"></a><a href="https://www.linkedin.com/" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="https://www.linkedin.com/in/mohammadfallahnejad/" height="40" width="60" /></a>
