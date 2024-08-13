---
link: "[[Study - OpenCV]]"
tags:
  - uncompleted
---
# 1. Transform image - black and white

### ( Convert code into words )
1. import cv2
2. Convert the image data in the path of input to a numpy array, Store it in a variable
3. Convert the image data created from step2 to grayscale image data, Using cvtColor function
	- [[Property Constants]] : cv2.COLOR_BGR2GRAY
4. Show the array created from Step2 as image on Window
5. Show the array created from Step3 as image on Window
6. Wait for n ms time a key to be entered
7. Destroy all windows created in executing code
### ( Code )
```python
import cv2
img = cv2.imread('img.jpg')

dst = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

cv2.imshow('img', img)
cv2.imshow('gray', dst)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
### ( Result )
![[Pasted image 20240808214351.png]]


# 2. Transform image - blur1 - kernel

### [ Convert code into words ]
1. import cv2
2. Convert the image data in the path of input to a numpy array, Store it in a variable  
3. Apply a Gaussian Blur to the image data created from step 2 using three different kernel sizes: (3, 3), (5, 5), and (7, 7), and store them in separate variables.
4. Show the array created from Step 2 as an image on the Window.
5. Show the arrays created from Step 3 as images on separate Windows.
6. 6. Wait for `n ms` time for a key to be entered.`
7. Destroy all windows created in executing the code.

### [ Code ]
```python
import cv2

img = cv2.imread ('img.jpg')

kernel_3 = cv2.GaussianBlur (img, (3, 3), 0)
kernel_5 = cv2.GaussianBlur (img, (5, 5), 0)
kernel_7 = cv2.GaussianBlur(img, (7, 7), 0)

cv2.imshow('img', img) 
cv2.imshow('kernel_3', kernel_3) 
cv2.imshow('kernel_5', kernel_5) 
cv2.imshow('kernel_7', kernel_7) 
cv2.waitKey(0) 
cv2.destroyAllWindows()
```
### [ Result ]
![[Pasted image 20240808231848.png]]
# 3. Transform image - blur1 - Sigma

### [ Convert code into words]
1. import cv2
2. Convert the image data in the path of input to a numpy array, Store it in a variable  
3. Apply a Gaussian Blur to the image data created from step 2 using three different sigma values: 1, 2, and 3, and store them in separate variables.
4. Show the array created from Step 2 as an image on the Window.
5. Show the arrays created from Step 3 as images on separate Windows.
6. Wait for `n ms` time for a key to be entered.
7. Destroy all windows created in executing the code.

### [ Code ]

```python
import cv2
img = cv2. imread('img.jpg')

sigma_1 = cv2.GaussianBlur(img, (0, 0), 1)
sigma_2 = cv2.GaussianBlur(img, (0, 0), 2)
sigma_3 = cv2.GaussianBlur(img, (0, 0), 3)

cv2.imshow('img', img)
cv2.imshow('sigma_l', sigma_1) 
cv2.imshow('sigma_2', sigma_2)
cv2.imshow('sigma_3', sigma_3) 
cv2.waitKey(0) 
cv2.destroyAllWindows()
```

### [ Result ]
![[Pasted image 20240808231422.png]]
# 4. Image Transform - Perspective1

**Expand the trapezoidal image**
### [ Convert code into words ]

1. import cv2
2. Convert the image data in the path of input to a numpy array, Store it in a variable  
3. Define the dimensions for the output image (width and height), and specify the source (`src`) and destination (`dst`) points for the perspective transformation.
4. Calculate the perspective transformation matrix from the source and destination points.
5. Apply the perspective transformation to the image using the transformation matrix, and store the result in a new variable.
6. Show the array created from Step 2 as an image on the Window.
7. Show the array created from Step 5 as an image on a separate Window.
8. Wait for `n ms` time for a key to be entered.
9. Destroy all windows created in executing the code.

### [ Code ]

```python
import cv2
import numpy as np

img = cv2.imread('newspaper.jpg')

width, height = 640, 240

src = np.array([[511, 352], [1008, 345], [1122, 584], [455, 594]], dtype=np.float32)
dst = np.array([[0, 0], [width, 0], [width, height], [0, height]], dtype=np.float32)

matrix = cv2.getPerspectiveTransform(src, dst)
result = cv2.warpPerspective(img, matrix, (width, height))

cv2.imshow('img', img)
cv2.imshow('result', result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### [ Result ]

![[Pasted image 20240808225816.png]]
# 5. Image Transform - Perspective2

**Standing rotated images correctly**

## [ Convert code into words ]

1. import cv2
2. Convert the image data in the path of input to a numpy array, Store it in a variable
1. Define the dimensions for the output image (width and height), and specify the source (`src`) and destination (`dst`) points for the perspective transformation.
2. Calculate the perspective transformation matrix from the source and destination points.
3. Apply the perspective transformation to the image using the transformation matrix, and store the result in a new variable.
4. Show the array created from Step 2 as an image on the Window.
5. Show the array created from Step 5 as an image on a separate Window.
6. Wait for `n ms` time for a key to be entered.
7. Destroy all windows created in executing the code.

## [ Code ]
```python
import cv2
import numpy as np

img = cv2.imread('poker.jpg')

width, height = 530, 710

src = np.array([[702, 143], [1133, 414], [726, 1007], [276, 700]], dtype=np.float32)
dst = np.array([[0, 0], [width, 0], [width, height], [0, height]], dtype=np.float32)

matrix = cv2.getPerspectiveTransform(src, dst)
result = cv2.warpPerspective(img, matrix, (width, height))

cv2.imshow('img', img)
cv2.imshow('result', result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### [ Result ]
![[Pasted image 20240808230744.png]]
![[Pasted image 20240808230654.png|400]]


# Python Syntax and Function

| Name                          | Category     | Input                                                                         | Return (or Result)                             | Explain it in my own words                                                                                                                             | Important Execution Code                                                                                                                                                              |
| ----------------------------- | ------------ | ----------------------------------------------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cv2.cvtColor()`              | `cv2.function` | (src, code)                                                                     | Color converted image                          | Converts an image from one color space to another. In this case, from BGR (default in OpenCV) to grayscale.                                                                                   | `code` specifies the conversion type: `cv2.COLOR_BGR2GRAY` converts BGR to grayscale.                                                                                               |
| `cv2.GaussianBlur()`          | `cv2.function` | (src, ksize, sigmaX)                                                            | Blurred image                                 | Applies Gaussian blur to an image, which smooths the image by averaging pixels within a kernel size. `ksize` determines the size of the kernel, and `sigmaX` controls the blur strength.       | `ksize` determines the kernel size (e.g., `(3, 3)`, `(5, 5)`); `sigmaX` controls the amount of blur.                                                                              |
| `cv2.getPerspectiveTransform()`| `cv2.function` | (src_points, dst_points)                                                         | Transformation matrix                         | Computes the perspective transform matrix needed to warp an image from the source points to the destination points.                                                                                 | `src_points` and `dst_points` are arrays of corresponding points in the source and destination images.                                                                                   |
| `cv2.warpPerspective()`       | `cv2.function` | (src, M, dsize)                                                                  | Warped image                                  | Applies a perspective transformation to an image using the transformation matrix `M`. `dsize` specifies the size of the output image.                                                            | `M` is the perspective transform matrix; `dsize` is the size of the output image.                                                                                                     |

### Explanation of Important Execution Code:

1. **Color Conversion (`cv2.cvtColor()`)**:
   - **Conversion Code**: `cv2.COLOR_BGR2GRAY` converts an image from BGR (color) to grayscale. This reduces the image to shades of gray, simplifying it for processing or analysis.

2. **Gaussian Blurring (`cv2.GaussianBlur()`)**:
   - **Kernel Size**: The `ksize` parameter determines the size of the Gaussian kernel. A larger kernel size results in a more significant blur.
   - **Sigma**: `sigmaX` controls the amount of Gaussian blur. A higher value creates a stronger blur effect.

3. **Perspective Transformation (`cv2.getPerspectiveTransform()`, `cv2.warpPerspective()`)**:
   - **Perspective Matrix**: `cv2.getPerspectiveTransform()` computes the matrix needed to transform an image based on given source and destination points.
   - **Warping**: `cv2.warpPerspective()` uses the computed matrix to warp the image to fit the new perspective.

### Examples:

- **Convert to Grayscale**: `dst = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)`
- **Apply Gaussian Blur**: `kernel_3 = cv2.GaussianBlur(img, (3, 3), 0)`
- **Perspective Warp**: 
  ```python
  matrix = cv2.getPerspectiveTransform(src, dst)
  result = cv2.warpPerspective(img, matrix, (width, height))
  ```
