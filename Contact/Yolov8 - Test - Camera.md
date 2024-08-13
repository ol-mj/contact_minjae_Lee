# Execution Process

### ( 0. Create a virtual environment for Yolov8 )

[ path : C:\Users\olmj\anaconda3\envs ]
어떻게 다운 받았는지 찾기
- 아이클라우드 들어가기
![[Pasted image 20240809132513.png]]



### ( 1. Open Conda Prompt )
![[Pasted image 20240809123956.png]]

![[Pasted image 20240809124134.png]]

1. Excute the anaconda prompt
2. Activate the yolov8 virtual environment.
3. Run the yolov8_camera_test_olmj.py file using the Python interpreter

### ( 2. yolov8_camera_test_olmj.py Code )

![[Pasted image 20240809123936.png]]
- path : C:\Users\olmj\Desktop
```python
from ultralytics import YOLO
import cv2

model = YOLO("yolov8s.pt")
cap = cv2.VideoCapture(0);

while cap.isOpened() :

    ret, frame = cap.read()
    if ret :
        results = model(frame)
        cv2.imshow("Results", results[0].plot())

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break


cv2.destroyAllWindows()
cap.release()
```
# Result
![[Pasted image 20240808234919.png]]
![[Pasted image 20240809121828.png]]