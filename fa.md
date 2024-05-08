<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>
<h1 align="center">آنالیز چهره🤗</h1>

<p align="center">
<img src="https://github.com/jokernets/facemesh/blob/main/images.jpeg">
</p>


### 🌏 مطالعه مقاله [English](https://github.com/jokernets/facemesh/blob/main/Fa.md)


<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>
<p align="center">
<img src="https://img.shields.io/badge/language-python-blue?style"/><img src="https://img.shields.io/github/stars/jokernets/audiotoplot"/><img src="https://img.shields.io/github/forks/jokernets/audiotoplot"/>
</p>

   


<h5 align="center">کلا 5 دقیقه نیاز داری بخونیش 😎</h5>

فهرست مطالب✅✔
==================

<!--ts-->
* 🔸[نصب کن⚠]()

 * 🔸[آنالیز کد📈]()
   * 🥇[] ()
   * 🥇[VideoCapture] (#set-variable)
   * 🥇[ت]()
   * 🥇[آن را اجرا کنید!](selot)

      * 🤍[نحوه استفاده](#نحوه استفاده-)
  
* 🔸[مثال بیشتر💯](#بیشتر-مثال-و-ویترین-)
   * 🥇[ویدئو پروژه📺](#ویدیو-تصویر-برنامه-)

   * [فایل exe پروژه]()

 * 🎁[🎃ارتباط با من](#connect-me)
<!--te-->

# نصب⚠

## کتابخانه را با pip نصب کنید:

```python
pip install opencv-python
pip install mediapipe
```
نصب موجود را به روز کنید: `pip3 install (کتابخانه شما) -- ارتقاء`
(تا حد امکان به روز رسانی کنید زیرا این کتابخانه در حال توسعه فعال است)

# آنالیز کد 😍:

## ورودی ها ♻🔰:

```python
import cv2
import mediapipe as mp
```
## `VideoCapture`:
1️⃣`cam = cv2.VideoCapture(0)`: این خط وب کم را فعال می کند. عدد 0 به معنای اولین دوربین متصل به سیستم است.

2️⃣`width = int(cam.get(cv2.CAP_PROP_FRAME_WTH))` و `height = int(cam.get(cv2.CAP_PROP_FRAME_HEIGHT))`: این دو خط فریم های ویدیو را تصویر می کنند.

3️⃣`cam.set(cv2.CAP_PROP_FPS, 30)`: این خط تعداد فریم در ثانیه (FPS) را 30 می کند.

4️⃣`cam.set(cv2.CAP_PROP_FOURCC, cv2.VideoWriter_fourcc(*'MJPG'))`: این خط کدک ویدیو را روی MJPG تنظیم می کند.

`faceMesh = mp.solutions.face_mesh.FaceMesh(False,1,True,0.5,0.5)`: این خط یک فیس مش ایجاد می کند که برای تشخیص کلیدهای چهره استفاده می شود.

5️⃣`mpDraw = mp.solutions.drawing_utils`: این ابزار خطی را که برای ترسیم نقاط کلیدی صورت روی فریم های ویدئو استفاده می شود، ترسیم می کند.

6️⃣`drawSpecCircle = mpDraw.DrawingSpec(ضخامت=1، دایره_شعاع = 1، رنگ=(0,255,0))` و `drawSpecLine = mpDraw.DrawingSpec(ضخامت=1, دایره_شعاع = 1, رنگ=(255,0,0) )`: این دو خط مشخصات، نقاط و خطوط را ترسیم می کنند. رنگ به عنوان RGB تعریف می شود. در اینجا نقاط سبز و خطوط قرمز خواهند بود.
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
## تابع 🔧⚒️:
- `_, frame = cam.read()`: این خط یک فریم از ویدیو را می خواند.
- `frameRGB = cv2.cvtColor(frame,cv2.COLOR_BGR2RGB)`: این خط رنگ فریم را از BGR به RGB تغییر می دهد. این تغییر ضروری است زیرا OpenCV فریم ها را با فرمت BGR می خواند، اما Mediapipe به فرمت RGB نیاز دارد.
- `results = faceMesh.process(frameRGB)`: این خط فریم را به مدل تشخیص چهره منتقل می کند و نتایج را دریافت می کند.
- `if results.multi_face_landmarks != None`: این خط بررسی می کند که آیا یک چهره در کادر شناسایی شده است.
- `for faceLandmarks in results.multi_face_landmarks`: این حلقه برای هر چهره شناسایی شده در کادر اجرا می شود.
- `connections= mp.solutions.face_mesh_connections.FACEMESH_...`: این خطوط نقاط اتصال بین نقاط کلیدی چهره را مشخص می کنند.
- `mpDraw.draw_landmarks(frame,faceLandmarks,connections,drawSpecCircle,drawSpecLine)`: این خط نقاط کلیدی و خطوط اتصال را روی قاب ترسیم می کند.
- `cv2.imshow('jokernets', frame)`: این خط فریم را نمایش می دهد.
- `if cv2.waitKey(1) & 0xff == ord('q')`: این خط بررسی می کند که آیا کاربر کلید 'q' را فشار داده است یا خیر. اگر کاربر کلید 'q' را فشار دهد، حلقه به پایان می رسد و برنامه به پایان می رسد.
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
## «اجراکن!» :
➖`cam.release()`: این خط دوربین را آزاد می کند. پس از آزاد شدن دوربین، دیگر نمی توان از آن برای خواندن فریم های ویدئویی استفاده کرد.
➖ `cv2.destroyAllWindows()`: این خط تمام پنجره های باز شده توسط OpenCV را می بندد. اگر هیچ پنجره ای باز نباشد، این خط تاثیری ندارد.
### چطوری استفادخ کنم؟ :
- run `main.py` with [requirments](https://github.com/jokernets/facemesh/blob/main/requirments.md)

```python
cam.release()
cv2.destroyAllWindows()
```
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>

## فایل exe از پروژه :
[دانلود فایل Exe]()



## More Examples and Showcase 👑

### Video image of the APP 📺


# `𝐂𝐨𝐧𝐧𝐞𝐜𝐭 𝐌𝐞`🎈🎃

<a herf="https://www.buymeacoffee.com/jokernets"><img src="https://cdn.buymeacoffee.com/buttons/v2/arial-yellow.png" alt="Buy Me A Coffee" width="180px">
<a href="mailto:joker.until33@gmail.com"><img align="center" width="60px" src="https://github.com/edent/SuperTinyIcons/raw/master/images/svg/gmail.svg" style="max-width: 100%;"></a><a href="https://www.linkedin.com/" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="https://www.linkedin.com/in/mohammadfallahnejad/" height="40" width="60" /></a>
