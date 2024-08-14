# 1. Reading 
Reading options
1. cv2.IMREAD_COLOR : 컬러 이미지
2. cv2.IMREAD_GRAYSCALE : 흑백 이미지
3. cv2.IMREAD_UNCHANGED : 투명 영역까지 포함
## [ Convert code into words ]
1. import the neccesary module
2. Create an array of images using the cv2.imread function and Read the image using the read options of color, gray, or unchanged in the second parameter field
3. Represent each of the created arrays in the window with their respective names.
4. Wait for n ms time key to be entered
5. Destroy all windows during excuting code

## [ Code ]
```python
import cv2
img_color = cv2.imread('img.jpg', cv2.IMREAD_COLOR)
img_gray = cv2.imread('img.jpg', cv2.IMREAD_GRAYSCALE)
img_unchanged = cv2.imread('img.jpg', cv2.IMREAD_UNCHANGED)

cv2.imshow('img.jpg', img_color)
cv2.imshow('img.jpg', img_gray)
cv2.imshow('img_unchanged', img_unchanged)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
## [ Result ]

![[Pasted image 20240805143730.png]]

# 2. Check the shape of the array

## [ Convert code into words ]
1. import the necessary module.
2. Use cv2.imread to get the images as an array.
3. Use the array's method, shape.

## [ Code ]
```python
import cv2
img = cv2.imread('img.jpg')
img.shape
```

## [ Result ]
(427, 640, 3)



# 3. Analyzing code
## [ TABLE ]



| Name                   | Category     | Input                                                         | Return (or Result)                                                                    | Explain it in my own words                                                                                                                                                                                 |
| ---------------------- | ------------ | ------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| cv2.imread()           | cv2.function | file_path                                                     | <class'numpy.ndarray'>                                                                | It takes an image file as input and converts the data in that image into a numpy.ndarray array.                                                                                                            |
| cv2.imshow()           | cv2.function | (Window_title, NumPy array)                                   | Return : nothing / Result : show display image on the screen                          | It takes an array of ndarray and displays them through the window gui. If you don't use a function that has a behavior that terminates windows, such as destroyAllWindow(), the kernel will have problems. |
| cv2.waitKey()          | cv2.function | Int (Time units : ms) if there is 0, action excute infinitely | Return : ASCII code, Int If there is no input, function return -1                     | The code's action terminates when the key is entered or when the time equal to the input value has elapsed. If a key is entered, return the integer corresponding to the key.                              |
| cv2.destroyAllWindow() | cv2.function | X                                                             | Result : Turn off all windows that were turned on in the process of running that code | Shut down any windows **that are running.**                                                                                                                                                                |
| ndarray.shape          | Method       | X                                                             | return : (row, column, channel) The data structure is a tuple                         | The number of elements in the tuple describes the dimensions of the array, where each element represents a row, column, and channel in this example.                                                       |

## [ Output of each piece cof code and the entire file ]
### ( Line-by-line output )

code flow Interpretation (time series) 
### ( Synthesize and summarize )


# Debug

| Code1 | ![[Pasted image 20240724163059.png]] | ![[Pasted image 20240724162726.png]]<br>![[Pasted image 20240724163406.png]] |
| ----- | ------------------------------------ | ---------------------------------------------------------------------------- |
| Code2 | ![[Pasted image 20240724163425.png]] | ![[Pasted image 20240724163337.png]]![[Pasted image 20240724163413.png]]     |
| Code3 | ![[Pasted image 20240724163952.png]] | ![[Pasted image 20240724164054.png]]![[Pasted image 20240724164202.png]]     |
## Why is only the code in the 3rd row working?

| Code1 | ![[Pasted image 20240724163059.png]] | ![[Pasted image 20240724162726.png]]<br>![[Pasted image 20240724163406.png]] |
| ----- | ------------------------------------ | ---------------------------------------------------------------------------- |
| Code2 | ![[Pasted image 20240724163425.png]] | ![[Pasted image 20240724163337.png]]![[Pasted image 20240724163413.png]]     |
| Code3 | ![[Pasted image 20240724163952.png]] | ![[Pasted image 20240724164054.png]]![[Pasted image 20240724164202.png]]     |

### 1 code

```python
import cv2

img = cv2.imread('img.jpg')
cv2.imshow('img', img)
cv2.destroyAllWindows()
```

Result: img turns on and off very quickly

### 2 times code
```python
import cv2

img = cv2.imread('img.jpg')
cv2.imshow('img', img)
key = cv2.waitKey(0)
```

Result: the kernel dies. Probably because there is no way to turn off the window.

### 3번 code

```python
import cv2

img = cv2.imread('img.jpg')
cv2.imshow('img', img)
```

Result: window turns on, but the kernel dies. Probably because there is no way to turn off the window.
