---
link: "[[Study - OpenCV]]"
tags:
  - dataview
  - uncompleted
---

# 1. Video file output

## [ Convert code into words ]
1. import the cv2 module.
2. Create an instance that receives input from a video file.
3. Pass in a video file and check if the file is associated with an object (using a while statement).
4. Read the frames stored in the time series by Using the instance's methods to sequentially 
5. When all frames have been read, print that there are no more frames to fetch and exit the loop.
6. Output each frame to a GUI with the window name "video".
7. if I press the key q, exit the loop after printing ,print to terminate by user input.

## [ Code ]

```python
import cv2
cap = cv2.VideoCapture('video.mp4') 
#[cv2_class :: cv2.VideoCaputure('video.mp4')]

while cap.isOpened():
	ret, frame =  cap.read # [cv2_function :: cap.read()]
	if not ret: #0이면 실행한다.
		print('No more frame')
		break #[function :: break]
	cv2.imshow('video', frame)
	if cv2.waitKey(1) == ord('q'): #[function :: ord()]
		print('Exit by User')
		break

cap.release() #[cv2_class :: cv2.VideoCapture_function]
cv2.destroyAllWindows()
```
## [ Result ]
1. When the video is over and exited
A video appears
![[Pasted image 20240805145148.png]]
The video ends and a string is printed
No more frame
2. When I press q during a video 
Print Exit by user

cv2.imread에서 return값의 구조와 예시를 알려줘

 cv2.imread 함수는 이미지 파일을 읽어 numpy 배열로 반환합니다. 반환되는 numpy 배열은 이미지의 픽셀값을 포함하고 있습니다.

예를 들어, 아래는 cv2.imread 함수를 사용하여 이미지 파일을 읽고 해당 이미지의 픽셀값을 출력하는 예시 코드입니다.

```python
import cv2

# 이미지 파일을 읽기
image = cv2.imread('example.jpg')

# 이미지의 픽셀값 출력
print(image)
```

위 코드를 실행하면, 해당 이미지 파일의 픽셀값이 출력됩니다. 이때 반환되는 numpy 배열은 (높이, 너비, 채널)의 형태를 가지며, 채널 값은 BGR 순서로 되어 있습니다.

# 2. Camera output 

## [ Convert code into words ]
1. import the cv2 module.
2. Create a VideoCapture instance. Here, input is the frame and video input from the webcam.
3. Exit Python if you don't have a good connection to the input data.
4. Call the instance's method to assign the frame and whether the action was successful to a variable.
5. exit if the behavior didn't work (exit = exit the loop) (run = continue the loop)
6. display the frame in a window.
7. free the input data assigned to the object.
8. terminate any Windows created by cv2 as the code progresses.
## [ Code ]

```python
import cv2
cap = cv2.VideoCapture(0)

if not cap.isOpened():
	exit()

while True:
	ret, frame = cap.read()
	if not ret:
		break
	cv2.imshow('camera', frame)
	if cv2.waitKey(1) == ord('q')
		break

cap.release()
cv2.destroyAllWindows()
```


## [ Result ]

![[Pasted image 20240805171454.png]]

# Analyzing Code
## [ Table ]

| Name                        | Category        | Input                                              | Return (or Result)                                                    | Explain it in my own words                                                                                                                                                                                                           |
| --------------------------- | --------------- | -------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| cv2.VideoCapture()          | cv2.Class       | Video type (file format (mp4) or dynamic (webcam)) | instance                                                              | The Video Capture class is responsible for opening a video file or camera device to read in video frames.                                                                                                                            |
| cv2.VideoCapture.isOpened() | cv2.Method      | X                                                  | **Boolean** / Ture,  False                                            | In this Method, True means that the video file was successfully connected. False means that There may be a problem with the file's connectivity. **The open state does not mean that the frames in the movie file are progressing.** |
| cv2.VideoCapture.read       | cv2.Method      | X                                                  | Tuple (Boolean, ndarray)                                              | The First element means Whether instance success to read a Frame by returning Boolean, The Second element means Image data from the frame read by the lead function In ndarray format                                                |
| cv2.VideoCapture.release    | cv2.Method      | X                                                  | The input I entered when creating an instance of the class is deleted | The video data used to create the instance is deallocated. However, instances of the class don't disappear. They are retained unless they are related to the input used to create the instance.                                      |
| break                       | python.function | X                                                  | X                                                                     | 반복문을 탈출한다. if문같은 조건문은 관련이 없다, 해당 조건문은 각 반복마다의 액션을 뜻한다.                                                                                                                                                                               |
| ord                         | python.function | string                                             | int                                                                   | 해당 동작에서는 ord('q')는 q에 할당된 숫자를 표현해주는 것과 같다. q에 대응되는 ASCII 숫자를 쳐도 결과는 똑같을 것이다                                                                                                                                                          |
| exit                        | python.function | 0 (exit code)                                      | X                                                                     | 인터프리터를 종료한다.                                                                                                                                                                                                                         |

## [ Output of each piece of code and the entire file ]




```dataview
TABLE without ID function
FROM "Practice2 - Video output.md"
```



# Common sense Note
Lg gram Webcam data format :  AVI or MP4