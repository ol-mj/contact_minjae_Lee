---
link: "[[Study - OpenCV]]"
tags:
  - uncompleted
---
# 1. resize 
## [ Set to fixed size ]

### ( Convert code into words )
1. import the necessary module
2. Convert the image files in the path you entered into a numpy array and assign this to variable
3. Create an array corresponding to the image data, fixing the number of each array horizontally and vertically and transforming it accordingly. assign the return value to a variable with a different name than in step2.
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all Windows that created in executing code 
- The features of an image can be deformed, but no features can be cut off or disappear.
### ( Code )

```python
import cv2

img = cv2.imread('img.jpg')
dst = cv2.resize(img, (400, 500))

cv2.imshow('img', img)
cv2.imshow('dst', dst)
cv2.waitkey(n)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240805223439.png|500]]

## [ Set as a ratio ]

### ( Convert code into words )
1. import the necessary module
2. Convert the image file in the path you entered into a numpy array and assign this to variable.
3. Resize the width and height of the array representing the image data
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all Windows that created in executing code
- [ ] Test: Find out what ratio function is talking about here

### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')
dst = cv2.resize(img, None, fx=2, fy=2)

cv2.imshow('img', img)
cv2.imshow('resize', dst)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240805223643.png|400]]

## [ Interpolation ]

> **Interpolation is a technique used when scaling or transforming an image.**
> 1. cv2.INTER_AREA : Use to reduce size
> 2. cv2.INTER_CUBIC: Use to increase size (slower, better quality)
> 3. cv2.INTER_LINEAR : Use to increase size (Default)
### ( Image - Apply interpolation to reduce )

#### < Convert code into words >
1. import the necessary module
2. Create an array that had an image information from the path entered
3. Apply an interpolation method that uses a ratio to resize. (The size of the ratio is set to the value that will be scaled down, Use the AREA method).
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all Windows that created in executing code
#### < Code >
```python
import cv2
img = cv2.imread('img.jpg')
dst = cv2.resize(img, None, fx=0.5, fy=0.5, interpolation=cv2.INTER_AREA)

cv2.imshow('img', img)
cv2.imshow('resize', dst)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
#### < Result >
![[Pasted image 20240805224909.png]]

### ( Image - Apply interpolation to make Bigger )
#### < Convert code into words >
1. import the necessary module
2. Create an array that had an image information from the path entered
3. Apply an interpolation method that uses a ratio to resize. (The size of the ratio is set to the value that will be scaled up, Use the CUBIC method).
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all Windows that created in executing code

#### < Code >
```python
import cv2
img = cv2.imread('img.jpg')
dst = cv2.resize(img, None, fx=2, fy=2, interpolation=cv2.INTER_CUBIC)

cv2.imshow('img', img)
cv2.imshow('resize', dst)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

#### < Result >
![[Pasted image 20240805225123.png]]


### ( Video - Set to fixed size )
#### < Convert code into words >
1. import  the necessary module
2. Create an instance that can receive the desired video data from the path and read information from the video frames
3. If the instance and video data are successfully connected, repeat the actions below.
	- Assign the instance's frame and whether the read was successful to a variable.
	- Exit the iteration if the data connection was not successful
	- Use the functions in cv2 to fix the width and height of that image frame, the. Assign the return value to Variable 
		- (apply any interpolation you like, as long as it meets the conditions)
	- Display an image with a fixed width and height above Window named 'video'
	- If I enter the value q key, it will escape the loop.
4. Release the video data allocated to the instance
5. Destroy all Windows that created in executing code

#### < Code >
```python
import cv2
cap = cv2.VideoCapture('video.mp4')

while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break

    frame_resized = cv2.resize(frame, (400, 500))
    cv2.imshow('video', frame_resized)
    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```
#### < Result >
![[Pasted image 20240806104818.png|400]]
The video plays with the fixed size

### ( Video - Set as a ratio )
#### < Convert code into words >
1. import the necessary module
2. Create an instance that can receive the desired video data from the path and read information from the video frames
3. If the instance and video data are successfully connected, repeat the actions below.
	- Assign the instance's frame and whether the read was successful to a variable.
	- Exit the iteration if the data connection was not successful
	- Use the functions in cv2 to adjust the aspect ratio to adjust the width and length of that image frame by interpolation(INTER_CUBIC), Assign the return value to Variable
	- Display an image with a fixed width and height above Window named 'video'
	- If I enter the value q key, it will escape the loop.
4. Release the video data allocated to the instance
5. Destroy all Windows that created in executing code

#### < Code >
```python
import cv2
cap = cv2.VideoCapture('video.mp4')

while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break

    frame_resized = cv2.resize(frame, None, fx=1.5, fy=1.5, interpolation=cv2.INTER_CUBIC)
    cv2.imshow('video', frame_resized)
    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```
#### < Result >
![[Pasted image 20240806105417.png]]

# 2. Crop the image
## [ Convert code into words ]
1. import the necessary module
2. Convert the image data in the path of input to a numpy array of data and store it in a variable.
3. From the array you received in Step 2, slice the rows and columns of the desired area and save them in a new variable.
4. Show the variables created in Step 2 and Step 3 as images in different windows with the name of the desired window.
5. Wait for n ms time a key to be entered
6. Destroy all Windows that created in executing code

100 to 200 for horizontal and 200 to 400 for vertical.
## [ Code ]
```python
import cv2
cap = cv2.VideoCapture('video.mp4')

while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break

    frame_resized = cv2.resize(frame, None, fx=1.5, fy=1.5, interpolation=cv2.INTER_CUBIC)
    cv2.imshow('video', frame_resized)
    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```
## [ Result ]
![[Pasted image 20240806105555.png|400]]

# 3. image symmetry
## [ Left and right Symmetry ]

### ( Convert code into words )
1. import the necessary module
2. Convert the image data in the path of input to a numpy array of data and store it in a variable
3. Use a function that converts the array representing the image data from Step 2 into an array representing images with left-right symmetry and store the return value in a new variable.
	- (For left-right symmetry, enter an integer greater than or equal to zero in the second argument of the function.)
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code

### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')
flip_horizontal = cv2.flip(img, 1)

cv2.imshow('img', img)
cv2.imshow('flip_horizontal', flip_horizontal)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240806111117.png]]

## [ Top-to-bottom symmetry ]

### ( Convert code into words )
1. import the necessary module
2. Convert the image data in the path of input to a numpy array of data and store it in a variable
3. Use a function that converts the array representing the image data from Step 2 into an array representing images with left-right symmetry and store the return value in a new variable.
	- (For Top-to-bottom symmetry, The second argument of the function input have to be a zero)
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code

### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')
flip_vertical = cv2.flip(img, 0)

cv2.imshow('img', img)
cv2.imshow('flip_vertical', flip_vertical)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240806110905.png]]

## [ Top, bottom, Left, Right symmetry ]

### ( Convert code into words )
1. import the necessary module
2. Convert the image data in the path of input to numpy array of data and store it in a variable
3. Use a function that converts the array representing the image data from Step 2 into an array representing images with left-right symmetry and store the return value in a new variable.
	- (For Top-to-bottom symmetry, The second argument of the function input have to be less than 0)
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code
### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')
flip_both = cv2.flip(img, -1)

cv2.imshow('img', img)
cv2.imshow('flip_both', flip_both)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240806111414.png]]

# 4.Rotate an image

## [ Rotate 90 degrees clockwise ]
### ( Convert code into words )
1. import the necessary module
2. Convert the image data in the path of input to numpy array of data and store it in a variable
3. Use a function that converts the array representing the image data from Step 2 into an array represneting images rotated 90 degrees(clockwise)  and store the return value in a new variable
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code
### ( Code )
```python
import cv2

img = cv2.imread('img.jpg')

rotate_90 = cv2.rotate(img, cv2.ROTATE_90_CLOCKWISE)

cv2.imshow('img', img)
cv2.imshow('rotate_90', rotate_90)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240806111736.png]]
## [ Rotate 180 degrees clockwise ]
### ( Convert code into words )
1. import the necessary module
2. Convert the image data in the path of input to numpy array of data and store it in a variable
3. Use a function that converts the array representing the image data from Step 2 into an array represneting images rotated 180 degrees(clockwise)  and store the return value in a new variable
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code
### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')

rotate_180 = cv2.rotate(img, cv2.ROTATE_180)

cv2.imshow('img', img)
cv2.imshow('rotate_180', rotate_180)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240808213453.png]]

## [ Rotate 90 degrees counterclockwise ]
### ( Convert code into words )
1. import the necessary module
2. Convert the image data in the path of input to numpy array of data and store it in a variable
3. Use a function that converts the array representing the image data from Step 2 into an array represneting images rotated 90 degrees(counter-clockwise)  and store the return value in a new variable
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code

### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')

rotate_270 = cv2.rotate(img, cv2.ROTATE_90_COUNTERCLOCKWISE)

cv2.imshow('img', img)
cv2.imshow('rotate_270', rotate_270)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### ( Result )

![[Pasted image 20240808213654.png]]

# Python Syntax and Function

| Name                          | Category     | Input                                                                                         | Return (or Result)                             | Explain it in my own words                                                                                                                                                       | Important Execution Code                                                                                                                                                   |
| ----------------------------- | ------------ | --------------------------------------------------------------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cv2.resize()`                | `cv2.function` | (src, dsize, fx, fy, interpolation)                                                           | Resized image                                  | Resizes the input image to a new size specified by `dsize` or scaling factors `fx` and `fy`. `interpolation` determines the resampling method.                               | `dsize` sets the new size of the image; `fx` and `fy` are scale factors; `interpolation` specifies the method (e.g., `cv2.INTER_AREA`, `cv2.INTER_CUBIC`).                  |
| `cv2.flip()`                  | `cv2.function` | (src, flip_code)                                                                             | Flipped image                                  | Flips the image around the specified axis. `flip_code` determines the axis for flipping: `0` for vertical, `1` for horizontal, and `-1` for both axes.                       | `flip_code` controls the direction of the flip: `0` (vertical), `1` (horizontal), `-1` (both).                                                                           |
| `cv2.rotate()`                | `cv2.function` | (src, rotate_code)                                                                           | Rotated image                                  | Rotates the image by 90, 180, or 270 degrees based on the `rotate_code`.                                                                                                      | `rotate_code` specifies the rotation angle: `cv2.ROTATE_90_CLOCKWISE`, `cv2.ROTATE_180`, `cv2.ROTATE_90_COUNTERCLOCKWISE`.                                               |
| `cv2.ROTATE_90_CLOCKWISE`     | `cv2.constant` | X                                                                                             | X                                              | Constant for rotating an image 90 degrees clockwise.                                                                                                                            | Use as a parameter in `cv2.rotate()` to rotate an image 90 degrees clockwise.                                                                                             |
| `cv2.ROTATE_180`              | `cv2.constant` | X                                                                                             | X                                              | Constant for rotating an image 180 degrees.                                                                                                                                       | Use as a parameter in `cv2.rotate()` to rotate an image 180 degrees.                                                                                                       |
| `cv2.ROTATE_90_COUNTERCLOCKWISE` | `cv2.constant` | X                                                                                             | X                                              | Constant for rotating an image 90 degrees counterclockwise.                                                                                                                     | Use as a parameter in `cv2.rotate()` to rotate an image 90 degrees counterclockwise.                                                                                       |

### Explanation of Important Execution Code:

1. **Resizing Images (`cv2.resize()`)**:
   - **Fixed Size**: When `dsize` is specified, the image is resized to the exact dimensions given.
   - **Scaling**: When `fx` and `fy` are provided, the image is scaled by these factors. For example, `fx=2` and `fy=2` doubles the width and height of the image.
   - **Interpolation**: Determines how pixel values are calculated during resizing. Methods like `cv2.INTER_AREA` and `cv2.INTER_CUBIC` affect the quality and performance of resizing.

2. **Flipping Images (`cv2.flip()`)**:
   - **Flip Code**: `flip_code` determines how the image is flipped:
     - `0`: Flip vertically.
     - `1`: Flip horizontally.
     - `-1`: Flip both vertically and horizontally.

3. **Rotating Images (`cv2.rotate()`)**:
   - **Rotation Code**: Specifies how the image is rotated:
     - `cv2.ROTATE_90_CLOCKWISE`: Rotate 90 degrees clockwise.
     - `cv2.ROTATE_180`: Rotate 180 degrees.
     - `cv2.ROTATE_90_COUNTERCLOCKWISE`: Rotate 90 degrees counterclockwise.

### Examples:

- **Fixed Size Resize**: `dst = cv2.resize(img, (400, 500))`
- **Scaling Resize**: `dst = cv2.resize(img, None, fx=2, fy=2)`
- **Interpolation Resize**: `dst = cv2.resize(img, None, fx=0.5, fy=0.5, interpolation=cv2.INTER_AREA)`
- **Flipping Horizontal**: `flip_horizontal = cv2.flip(img, 1)`
- **Rotating 90 Degrees Clockwise**: `rotate_90 = cv2.rotate(img, cv2.ROTATE_90_CLOCKWISE)`

