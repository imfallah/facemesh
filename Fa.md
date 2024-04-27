<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>
<h1 align="center">آنالیز صورت😎</h1>



### 🌏 مقاله به [English](README_fa.md)


<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif"><br><br>
<p align="center">
<img src="https://img.shields.io/badge/language-python-blue?style"/><img src="https://img.shields.io/github/stars/jokernets/audiotoplot"/><img src="https://img.shields.io/github/forks/jokernets/audiotoplot"/>
</p>

   


<h5 align="center">🛑زمان مطالعه 5 دقیقه⚠</h5>

فهرست مطالب✅✔
=================

<!--ts-->
   * 🔸[نصب کن !⚠](#installation)

   * 🔸[آنالیز کد 📈](#analiys-code-)
     * 💫[ماژول های ورودی✔](#importing)
     * 💫[✔](#set-variable)
     * 💫[✔](#audio-input)
     * 💫[✔](#define)
     * 💫[✔](#set-plot)
  
   * 🔸[ویترین💯](#more-examples-and-showcase-)
     * 🥇[ویدوی از پروژه📺](#video-image-of-the-app-)
    
   * 🎁[`ارتباط با من🎃`](#connect-me)
<!--te-->

# نصب کن! ⚠

## ماژول هارو با pip نصب کن:

```python
pip install opencv-python
pip install mediapipe
pip install tensorflow
pip install keras-models
```

Update existing installation:`pip3 install (YOUR LIBRARY) --upgrade`
(update as often as possible because this library is under active development)

# آنالیز کد 🎃:

## `ماژول های ورودی`♻🔰:
1.🔷 **کتابخانه های وارداتی**:

- `cv2`: OpenCV برای پردازش تصویر✅
      
- "mediapipe": کتابخانه ای برای ساخت مدل های ادراکی چندوجهی (مانند صورت، دست، اشاره).✅
      
- `tensorflow.keras.models`: مدل‌های Keras برای یادگیری ماشین.✅

2.🔷 **MediaPipe Face Mesh**:

- کد راه حل، **MediaPipe Face Mesh** را با استفاده از ماژول "mp_face_mesh" مقداردهی اولیه می کند.✅
- محلول Face Mesh برای تشخیص و ردیابی ویژگی‌های صورت (مانند چشم، بینی، دهان و غیره) در جریان‌های ویدیویی یا تصاویر بلادرنگ طراحی شده است.✅
- می توان از آن برای برنامه های مختلف از جمله تجزیه و تحلیل ویژگی های چهره، واقعیت افزوده و تشخیص حالت چهره استفاده کرد.✅

3.🔷 **نکته**:
- قطعه کد ارائه شده شامل هیچ عملکرد یا استفاده خاصی فراتر از وارد کردن ماژول های لازم و مقداردهی اولیه راه حل Face Mesh MediaPipe نیست.✅
- اگر وظایف یا الزامات خاصی در رابطه با تحلیل فیس مش دارید، لطفاً زمینه اضافی را ارائه دهید.✅
- در غیر این صورت قطعه کد خود عمل خاصی انجام نمی دهد.✅
```python
import cv2
import mediapipe as mp
from tensorflow.keras import models
mp_drawing = mp.solutions.drawing_utils
mp_drawing_styles = mp.solutions.drawing_styles
mp_face_mesh = mp.solutions.face_mesh

```
## `دوم`:
1.🔷 ** راه اندازی و پیکربندی **:
- کد راه حل **MediaPipe Face Mesh** را با پارامترهای خاص مقداردهی اولیه می کند:
- `static_image_mode=True`: نشان می دهد که راه حل تصاویر استاتیک را پردازش می کند (نه جریان های ویدیویی).
- `max_num_faces=1`: مشخص می کند که فقط یک چهره شناسایی می شود (اگر چند چهره در تصویر وجود دارد).
- `refine_landmarks=True`: پالایش موقعیت های شاخص را فعال می کند.
- `min_detection_ trust=0.5`: حداقل آستانه اطمینان را برای تشخیص چهره تنظیم می کند.

2.🔷 **پردازش تصویر**:
- برای هر فایل تصویری در لیست "IMAGE_FILES":
- تصویر را با استفاده از OpenCV (`cv2.imread`) بخوانید.
- تبدیل تصویر BGR به فرمت RGB (`cv2.cvtColor(تصویر، cv2.COLOR_BGR2RGB)`).
- تصویر را با استفاده از محلول Face Mesh ('face_mesh.process') پردازش کنید.
- اگر هیچ ویژگی خاصی از صورت شناسایی نشد، به تصویر بعدی ادامه دهید.
- یک کپی حاشیه نویسی از تصویر (` annotated_image`) ایجاد کنید.
- با استفاده از سبک های مختلف، علائم مش چهره را روی تصویر حاشیه نویسی بکشید:
- `FACEMESH_TESSELATION`: الگوی مش را ترسیم می کند.
- `FACEMESH_CONTOURS`: خطوط صورت را ترسیم می کند.
- "FACEMESH_IRISES": علائم عنبیه را ترسیم می کند.
- تصویر حاشیه نویسی شده را در یک فایل ذخیره کنید (به عنوان مثال، `/tmp/annotated_image0.png`).

3. 🔷**نکته**:
- قطعه کد فرض می کند که لیست "IMAGE_FILES" حاوی مسیرهای فایل تصویری معتبر است.
- محلول Face Mesh ویژگی های صورت (مانند چشم، بینی، دهان و غیره) را تشخیص داده و آنها را روی تصویر نشان می دهد.
- تصاویر حاشیه نویسی ذخیره شده ویژگی های صورت شناسایی شده را نشان می دهد.
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
## `سوم` :

1. 🔷**تنظیم اولیه**:
- متغیر "cap" با استفاده از "cv2.VideoCapture(0)" ایجاد می شود.
- "cv2.VideoCapture(0)" وب کم را برای گرفتن فریم های ویدئویی راه اندازی می کند.
- آرگومان "0" نشان می دهد که باید از دوربین پیش فرض (معمولاً وب کم داخلی) استفاده شود.
2.🔷**مشخصات طراحی**:
- متغیر 'drawing_spec' با پارامترهای خاصی ایجاد می شود:
- `thickness=1`: ضخامت خطوط مورد استفاده برای ترسیم نمادها را تنظیم می کند.
- `circle_radius=1`: شعاع دایره هایی را که برای ترسیم نمادها استفاده می شوند را تنظیم می کند.
3.🔷 **نکته**:
- کد فرض می کند که یک وب کم در دسترس و قابل دسترسی است.
- وب‌کم فریم‌های ویدیویی را می‌گیرد که می‌توان آن‌ها را با استفاده از راه‌حل Face Mesh یا سایر تکنیک‌های بینایی کامپیوتری پردازش کرد.
```python
# For webcam input:
drawing_spec = mp_drawing.DrawingSpec(thickness=1, circle_radius=1)
cap = cv2.VideoCapture(0)
```
## `چهارم` :  

1. 🔷** راه اندازی و پیکربندی **:
- کد راه حل **MediaPipe Face Mesh** را با پارامترهای خاص مقداردهی اولیه می کند:
- `max_num_faces=1`: مشخص می کند که فقط یک چهره شناسایی می شود (اگر چند چهره در کادر وجود دارد).
- `refine_landmarks=True`: پالایش موقعیت های شاخص را فعال می کند.
- `min_detection_spection=0.5`: حداقل آستانه اطمینان را برای تشخیص چهره تنظیم می کند.
- `min_tracking_ trust=0.5`: حداقل آستانه اطمینان را برای ردیابی چهره تنظیم می کند.

2. 🔷**پردازش فریم های ویدئویی**:
- کد وارد حلقه ای می شود که فریم های ویدئویی را از دوربین (وب کم) با استفاده از `cap.read()` می گیرد.
- اگر فریمی با موفقیت خوانده نشود، "نادیده گرفتن کادر خالی دوربین" را چاپ می کند و به فریم بعدی ادامه می دهد.
- تصویر از فرمت BGR به فرمت RGB (`cv2.cvtColor(image, cv2.COLOR_BGR2RGB)`) تبدیل شده است.
- محلول Face Mesh تصویر را با استفاده از "face_mesh.process(image)" پردازش می کند.
- اگر نشانه های چهره شناسایی شوند (`results.multi_face_landmarks`)، نشانه ها با استفاده از سبک های مختلف روی تصویر کشیده می شوند:
- `FACEMESH_TESSELATION`: الگوی مش را ترسیم می کند.
- `FACEMESH_CONTOURS`: خطوط صورت را ترسیم می کند.
- "FACEMESH_IRISES": علائم عنبیه را ترسیم می کند.
   - تصویر به صورت افقی برگردانده می شود تا سلفی نمایش داده شود (`cv2.flip(image, 1)`).
   - فریم پردازش شده در پنجره ای به نام "MediaPipe Face Mesh" نمایش داده می شود.
   - این حلقه تا فشار دادن کلید Esc (کلید کد 27) ادامه دارد.

3.🔷 **نکته**:
- کد فرض می کند که یک دوربین (وب کم) در دسترس و قابل دسترسی است.
- محلول Face Mesh نشانه های چهره را شناسایی کرده و آنها را روی فریم های ویدئویی تجسم می کند.
- کاربر می تواند با فشار دادن کلید 'Esc' پنجره را ببندد.
- قطعه کد استثناهای مربوط به دسترسی به دوربین یا خواندن فریم ویدیو را کنترل نمی کند.
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
