---
link: "[[Study - OpenCV]]"
tags:
  - uncompleted
---
# 1. Create an empty Sketch Book

## [ Convert code into words ]
1. Import the necessary libraries and modules.
2. Create a array that will contain 0 element all and properties, name of 'img', width, length, 3chnnel, unit8 
3. Print the Array representing image information on Window
4. Wait for n ms time a key to be entered
5. Destroy All Window created during executing code

## [ Code ]
```python
import cv2
import numpy as np

img = np.zeros((width int, length int, channel,int), dtype = np.uint)

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## [ Result ]

![[Pasted image 20240805172216.png|400]]

# 2. Change the Color of a part of Image
## [ Convert code into words ]
1. Import the necessary libraries and modules.
2. Create a array that had 0 element all and properties, name of 'img', width, length, 3chnnel, unit8
3. change the information in each element (a tuple in the data structure) corresponding to the horizontal and vertical dimensions of the array to data organized in the desired representation.
4. Print the transformed Array representing image information on Window
5. Wait for n ms time a key to be entered
6. Destroy All Window created during executing code

## [ Code ]
```python
import cv2
import numpy as np

img = np.zeros((512, 512, 3), dtype = uint8)
img[0:256, 256:512] = (255, 255, 255)

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
## [ Result ]
![[Pasted image 20240805173628.png|400]]

# 3. Draw straight lines

## [ Convert code into words ]
1. Import the necessary libraries and modules.
2. Create a array that will contain 0 element all and properties, name of 'img', width, length, 3channel, unit8
3. Store the color information of the straight line in a variable
4. Store the thickness information in a variable
5. Use the straight line function in the cv2 module.
6. Print the transformed Array representing image information on Window
7. Wait for n ms time a key to be entered
8. Destroy All Window created during executing code

## [ Code ]
```python
import cv2
import numpy as np

img = np.zeros((512, 512, 3), dtype = np.uint8)
COLOR = (255, 255, 0)
THICKNESS = 3

cv2.line(img, (0, 0), (400, 100), COLOR, THICKNESS, cv2.LINE_8)

cv2.imshow(img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
## [ Result ]
![[Pasted image 20240805173513.png|500]]
# 4. Draw a circle

## [ Convert code into words ]
1. import the necessary libraries modules.
2. Create a array that will cotain 0 element all and properties, name of 'img', width, length, 3channel, unit8
3. Store the Color information of the circle in a variable
4. Store the Radius information of the circle in a variable
5. Store the thickness information in a variable
6. Using the circle function in the cv2 moudle, Draw Hollow circles, Filled circle on the Array fished from Step2
7. Print the transformed Array representing image information on Window
8. Wait for n ms time a key to be entered
9. Destroy All Window created during executing code

## [ Code ]

```python
import cv2
import numpy as np

img = np.zeros((512, 512, 3), dtype = np.uint8)
COLOR = (0, 255, 0)
THICKNESS = 8
RADIUS = 20

cv2.circle(img, (400, 100), RADIUS, COLOR, THICKNESS, cv2.LINE_AA)

cv2.imshow('img_line',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## [ Result ]
![[Pasted image 20240805173953.png|400]]

# 5. Draw a Square
## [ Convert code into words ]
1. import the necessary modules and libraries
2. Create a array that will contain 0 element all and properties ( name of 'img', width, length, 3channel, unit8 )
3. Store the color information of the Square in a variable
4. Store the thickness information in a variable
5. Using the rectangle function in the cv2 module, Draw Hollow rectangle, Filled rectangle from Step2
6. Print the tranformed Array representing image information on Window
7. Wait for n ms time a key to be entered
8. Destroy All Window created during executing code
## [ Code ]
```python
import cv2
import numpy as np

img = np.zeros((512, 512, 3), dtype = np.uint8)
COLOR = (0, 255, 0)
THICKNESS = 8

cv2.rectangle(img, (100, 100), (300, 200), COLOR, THICKNESS, cv2.LINE_AA)

cv2.imshow('img_line',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## [ Result ]
![[Pasted image 20240805174327.png|400]]

# 6. Draw a Polyline
## [ Convert code into words ]
1. Import the necessary modules and libraries
2. Create a array that will contain 0 element all and properties ( name of 'img', width, length, 3channel, unit8 )
3. Store the color information of the Polyline in a variable
4. Store the thickness information in a variable
5. Store the vertex information for each polygon
6. Using the polylines function in the cv2 module, Draw two Polylines
7. Print the transformed Array representing image information on Window
8. Wait for n ms time a key to be entered
9. Destroy All Window created during executing code

## [ Code ]

```python
import cv2
import numpy as np

img = np.zeros((512, 512, 3), dtype = np.uint8)

COLOR = (0, 0, 255)
THICKNESS = 3

pts1 = np.array([[100, 100], [200, 100], [100, 200]])
cv2.polylines(img, [pts1], True, COLOR, THICKNESS, cv2.LINE_AA)

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## [ Result ]

![[Pasted image 20240805220007.png|400]]

# Python Function Table

| Name              | Category         | Input                                                        | Return (or Result)                    | Important Execution Code                                                                         | Explain it in my own words                                                                                                             |
| ----------------- | ---------------- | ------------------------------------------------------------ | ------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| `np.zeros()`      | `numpy.function` | Tuple specifying dimensions and data type (dtype)            | <class 'numpy.ndarray'>               | Initializes the array with zeros; uses `dtype` to specify the data type (e.g., `np.uint8`).      | Creates an array of the specified shape filled with zeros. The `dtype` determines the data type of the array elements.                 |
| `cv2.line()`      | `cv2.function`   | (image, start_point, end_point, color, thickness, line_type) | Modified image with a line drawn      | Uses `cv2.LINE_8` or `cv2.LINE_AA` for line type; modifies pixel values along the line.          | Draws a line on the image from `start_point` to `end_point` with the specified `color`, `thickness`, and `line_type`.                  |
| `cv2.circle()`    | `cv2.function`   | (image, center, radius, color, thickness, line_type)         | Modified image with a circle drawn    | Uses `cv2.LINE_AA` for antialiased circle edges; updates pixel values within the circle area.    | Draws a circle on the image centered at `center` with a specified `radius`, `color`, `thickness`, and `line_type`.                     |
| `cv2.rectangle()` | `cv2.function`   | (image, top_left, bottom_right, color, thickness, line_type) | Modified image with a rectangle drawn | Updates pixel values between `top_left` and `bottom_right`; `thickness` determines border width. | Draws a rectangle on the image with corners at `top_left` and `bottom_right` with the specified `color`, `thickness`, and `line_type`. |
| `cv2.polylines()` | `cv2.function`   | (image, points, is_closed, color, thickness, line_type)      | Modified image with a polygon drawn   | Draws lines between consecutive points; `is_closed` determines if the polygon should be closed.  | Draws a polygon on the image using the array `points`. `is_closed` indicates whether the polygon should be closed.                     |
| `cv2.imshow()`    | `cv2.function`   | (window_title, numpy_array)                                  | Displayed image on a window           |                                                                                                  | Shows the image in a window with the title specified by `window_title`. The image is displayed using the `numpy                        |
