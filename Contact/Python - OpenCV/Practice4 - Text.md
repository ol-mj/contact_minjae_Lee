---
link: "[[Study - OpenCV]]"
tags:
  - uncompleted
---
# The type of font used by Open CV

1. cv2.FONT_HERSHEY_SIMPLEX : 보통 크기의 산 세리프(sans-serif) 글꼴
2. cv2.FONT_HERSHEY_PLAIN : 작은 크기의 산 세리프 글꼴
3. cv2.FONT_HERSHEY_SCRIPT_SIMPLEX : 필기체 스타일 글꼴
4. cv2.FONT_HERSHEY_TRIPLEX : 보통 크기의 산 세리프 글꼴
5. cv2.FONT_ITALIC : 기울임 (이탤릭체)

# 1. Default
## [ Convert code into words ]
1. **Import the necessary module**: The code imports the required modules, `numpy` for numerical operations and `cv2` from OpenCV for image processing tasks.
2. **Create a black image canvas**: The code generates a blank image (a black canvas) with a resolution of 640x480 pixels and 3 color channels (RGB). The image is initialized to zero, meaning all pixels are black.
3. **Set text properties**: Several variables are set to define the scale, color, and thickness of the text that will be drawn on the image. The color is set to white (`(255, 255, 255)`), and the thickness is set to 1 pixel.
4. **Draw text on the image**: The `cv2.putText` function is used multiple times to draw different strings of text on the image using various font styles provided by OpenCV. Each call specifies the position, font, scale, color, and thickness of the text.
5. **Display the image with the drawn text**: The image with the drawn text is displayed in a window using the `cv2.imshow` function. The window will remain open until a key is pressed.
6. **Wait for a key press**: The `cv2.waitKey(0)` function causes the program to wait indefinitely until a key is pressed, allowing the user to view the image.
7. **Close the window**: After a key is pressed, all windows opened by OpenCV are closed using `cv2.destroyAllWindows`.
## [ Code ]
```python
import numpy as np
import cv2

img = np.zeros((480, 640, 3), dtype=np.uint8)

SCALE = 1
COLOR = (255, 255, 255)
THICKNESS = 1

cv2.putText(img, "olmj Simplex", (20, 50), cv2.FONT_HERSHEY_SIMPLEX, SCALE, COLOR, THICKNESS)
cv2.putText(img, "minjae Plain", (20, 150), cv2.FONT_HERSHEY_PLAIN, SCALE, COLOR, THICKNESS)
cv2.putText(img, "Lee Script Simplex", (20, 250), cv2.FONT_HERSHEY_SCRIPT_SIMPLEX, SCALE, COLOR, THICKNESS)
cv2.putText(img, "minjae Lee Triplex", (20, 350), cv2.FONT_HERSHEY_TRIPLEX, SCALE, COLOR, THICKNESS)
cv2.putText(img, "Lee min jae Italic", (20, 450), cv2.FONT_HERSHEY_TRIPLEX | cv2.FONT_ITALIC, SCALE, COLOR, THICKNESS)

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## [ Result ]
![[Pasted image 20240809225930.png]]
# 2. Bypass Korean

## [ Convert code into words ]

1. **Import the necessary modules**: The code imports the `numpy` module for numerical operations, `cv2` from OpenCV for image processing tasks, and `PIL` (Python Imaging Library) components (`ImageFont`, `ImageDraw`, `Image`) for handling fonts and drawing text on images.
2. **Define a custom function to draw text on an image**: The function `myPutText` takes an image (`src`), text (`text`), position (`pos`), font size (`font_size`), and font color (`font_color`). It converts the `src` image to a format that can be manipulated with PIL, draws the text using the specified font and color, and then converts the image back to a NumPy array.
3. **Create a black image canvas**: The code generates a blank image (a black canvas) with a resolution of 640x480 pixels and 3 color channels (RGB). The image is initialized to zero, meaning all pixels are black.
4. **Set text properties**: The font size is defined as 30 pixels, and the text color is set to white (`(255, 255, 255)`).
5. **Draw text on the image using the custom function**: The `myPutText` function is used to draw the text "이민재" at position `(20, 50)` on the image using the specified font size and color.
6. **Display the image with the drawn text**: The image with the drawn text is displayed in a window using the `cv2.imshow` function. The window will remain open until a key is pressed.
7. **Wait for a key press**: The `cv2.waitKey(0)` function causes the program to wait indefinitely until a key is pressed, allowing the user to view the image.
8. **Close the window**: After a key is pressed, all windows opened by OpenCV are closed using `cv2.destroyAllWindows`.
    
## [ Code ]

```python
import numpy as np
import cv2
from PIL import ImageFont, ImageDraw, Image

def myPutText(src, text, pos, font_size, font_color):
    img_pil = Image.fromarray(src)
    draw = ImageDraw.Draw(img_pil)
    font = ImageFont.truetype('fonts/gulim.ttc', font_size)
    draw.text(pos, text, font=font, fill=font_color)
    return np.array(img_pil)

img = np.zeros((480, 640, 3), dtype=np.uint8)

FONT_SIZE = 30
COLOR = (255, 255, 255)

img = myPutText(img, "이민재", (20, 50), FONT_SIZE, COLOR)

cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


## [ Result ]
![[Pasted image 20240809230956.png]]



# Python Syntax and Function

| Name                   | Category     | Input                                                                                   | Return (or Result)                                      | Explain it in my own words                                                                                                                                                  | Important Execution Code                                                                                                                                               |
| ---------------------- | ------------ | --------------------------------------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `cv2.putText()`        | `cv2.function` | (image, text, position, font, font_scale, color, thickness, line_type)                  | Modified image with text drawn                          | Adds text to the image at the specified `position` using the given `font`, `font_scale`, `color`, `thickness`, and optional `line_type`.                                      | `font` specifies the text style (e.g., `cv2.FONT_HERSHEY_SIMPLEX`); `font_scale` adjusts text size; `color` and `thickness` determine text appearance.                  |
| `Image.fromarray()`    | `PIL.Image`   | numpy_array                                                                             | <class 'PIL.Image.Image'>                               | Converts a NumPy array to a PIL image object, allowing for more advanced image manipulation.                                                                               | Creates a PIL Image object from the NumPy array to enable text drawing with PIL capabilities.                                                                           |
| `ImageDraw.Draw()`     | `PIL.ImageDraw`| PIL.Image object                                                                        | <class 'PIL.ImageDraw.Draw'>                             | Initializes a drawing context on a PIL image to enable drawing shapes and text.                                                                                             | Provides drawing functionality on the PIL Image object.                                                                                                                |
| `ImageFont.truetype()` | `PIL.ImageFont` | (font_path, font_size)                                                                  | <class 'PIL.ImageFont.FreeTypeFont'>                     | Loads a TrueType or OpenType font file and creates a font object with the specified `font_size`.                                                                            | Loads a font from the specified path with the given size, allowing for customized text appearance.                                                                    |
| `draw.text()`          | `PIL.ImageDraw`| (position, text, font, fill)                                                             | X                                                       | Draws text onto the PIL image at the specified `position` with the given `font` and `fill` color.                                                                           | Writes the text to the PIL Image at the defined position using the specified font and color.                                                                          |

