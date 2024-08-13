---
link: "[[Study - OpenCV]]"
tags:
  - uncompleted
---
# 1. Image Save
## [ Convert code into words ]

1. import the necessary module
2. Reads in an external image file, converts the data from that file to a grayscale image, and returns it as an array.
3. Wait n ms time a key to be entered
4. Destroy All Window created during executing code
5. Use a function that saves an array representing the images with the name you set to the desired path and assigns success or failure to a variable.
6. Print the Success or Failed

## [ Code ]
```python
import cv2
img = cv2.imread('img.jpg', cv2.IMREAD_GRAYSCALE)
cv2.imshow('img', img)
cv2.waitKey(0)
cv2.destroyAllWindows()

result = cv2.imwrite('img_save.jpg', img)
print(result)
```

## [ Result ]
![[Pasted image 20240805221448.png]]


**What if you want to save the image directly without displaying it?**
```python
import cv2
img = cv2.imread('Path to the desired image', cv2.IMREAD_GRAYSCALE)
result = cv2.imwrite('Path and name to save‘, Array with image information to store)
```
**Where is it stored?**

# 2. Image Storage formats

## [ Convert code into words ]
1. import the necessary module
2. Reads in an external image file, converts the data from that file to a grayscale image, and returns it as an array.
3. Use a function that saves an array representing the image with the name you set to the desired path, and assigns success to a variable. Here, you can rename the extension after the filename of the image and it will be saved in the changed format. (In this example, convert to png)
## [ Code ]

```python
import cv2
img = cv2.imread('img.jpg', cv2.IMREAD_GRAYSCALE)
cv2.imwrite('img_save.png', img)
```
## [ Result ]
png file format image

# 3. Video Save

## [ Convert code into words ]
1. import the necessary module
2. Create an instance of VideoCaputre(Class) connected with the video file
3. Return a four-digit code that refers to the DIVX codec to the variable. (Codec: How video files are compressed and decompressed)
4. Assign the width and fps of the frame using the functions in each cv2 (length should be rounded)
5. Create an instance using VideoWriter in cv2 module
	- VideoWriter(‘The file path where you want to save the video', codec series, fps, (width, height))
6. Once you have successfully connected to the video data, repeat the steps below.
	- Assigning video frames and read success to variables
	- Escape the loop at the end of the video
	- Save video data only (SoundX)
	- If I type q, it escapes the loop
7. Release the video data assigned to the instance
8. Destroy All Window created during executing code

## [ Code ]
```python
import cv2
cap = cv2.VideoCapture('video.mp4')

fourcc = cv2.VideoWriter_fourcc(*'DIVX')

width = round(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = round(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
fps = cap.get(cv2.CAP_PROP_FPS)

out = cv2.VideoWriter('output.avi', fourcc, fps, (width, height))

while cap.isOpened():
    ret, frame = cap.read()
    
    if not ret:
        break
    
    out.write(frame)
    cv2.imshow('video', frame)
    if cv2.waitKey(1) == ord('q'):
        break

out.release()
cap.release()
cv2.destroyAllWindows()
```

## [ Result ]
![[Pasted image 20240805221901.png]]

# Python Syntax and Function

| Name                       | Category     | Input                                                                                  | Return (or Result)                                      | Explain it in my own words                                                                                                                                                      | Important Execution Code                                                                                                                                                    |
| -------------------------- | ------------ | -------------------------------------------------------------------------------------- | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cv2.imwrite()`            | `cv2.function` | (file_path, numpy_array)                                                                | Boolean value indicating success (True or False)        | Saves an image to the specified file path. The `numpy_array` is written to a file, and the function returns `True` if the operation is successful, otherwise `False`.           | Writes the `numpy_array` image data to a file; the return value indicates whether the write operation was successful.                                                     |
| `cv2.VideoCapture()`       | `cv2.function` | (video_path)                                                                           | <class 'cv2.VideoCapture'>                              | Opens a video file or stream for reading. Returns a `VideoCapture` object used to interact with the video file or stream.                                                       | Initializes a video capture object for reading frames from a video file or stream.                                                                                          |
| `cv2.VideoWriter_fourcc()`  | `cv2.function` | (code)                                                                                 | Integer code for the codec                              | Specifies the codec used for video compression. The `fourcc` code is a four-character code that defines the codec (e.g., 'DIVX', 'XVID').                                       | Defines the codec to use for encoding the video file.                                                                                                                        |
| `cv2.VideoWriter()`        | `cv2.function` | (output_file, fourcc, fps, frame_size)                                                  | <class 'cv2.VideoWriter'>                               | Creates a `VideoWriter` object that writes video frames to a file with specified codec, frame rate, and resolution.                                                               | Initializes the video writer object with the codec, frame rate, and resolution.                                                                                           |
| `cap.get()`                | `cv2.method`  | Integer property identifier (e.g., `cv2.CAP_PROP_FRAME_WIDTH`)                        | Property value (e.g., width, height, fps)               | Retrieves the value of a specified property from the `VideoCapture` object.                                                                                                     | Used to get properties such as frame width, height, and frames per second (fps) from the video capture object.                                                              |
| `out.write()`              | `cv2.method`  | numpy_array (frame)                                                                     | X                                                       | Writes a frame to the video file using the `VideoWriter` object.                                                                                                                | Adds a frame to the video output file.                                                                                                                                      |
| `cap.read()`               | `cv2.method`  | X                                                                                      | Tuple (Boolean, numpy_array)                             | Reads the next frame from the video file. Returns a boolean indicating success and the frame data as a `numpy_array`.                                                             | Retrieves the next frame from the video capture object.                                                                                                                       |
| `out.release()`            | `cv2.method`  | X                                                                                      | X                                                       | Releases the `VideoWriter` object and finalizes the output video file.                                                                                                           | Ensures the video writer object is properly closed and the file is saved.                                                                                                    |
| `cap.release()`            | `cv2.method`  | X                                                                                      | X                                                       | Releases the `VideoCapture` object and frees resources associated with it.                                                                                                      | Closes the video capture object and releases any resources.                                                                                                                 |

### Explanation of Important Execution Code:

1. **Saving Images (`cv2.imwrite()`)**:
   - **File Path**: The `file_path` specifies where the image should be saved.
   - **Array with Image Information**: The `numpy_array` contains the image data to be written to the file.
   - **Return Value**: Returns `True` if the image was saved successfully, otherwise `False`.

2. **Video Processing**:
   - **Opening Video (`cv2.VideoCapture()`)**: Initializes a video capture object for reading from a file or stream.
   - **Codec (`cv2.VideoWriter_fourcc()`)**: Defines the codec used for encoding the video.
   - **Video Writing (`cv2.VideoWriter()`)**: Creates a video writer object for saving video frames to a file.
   - **Getting Video Properties (`cap.get()`)**: Retrieves properties such as frame width, height, and fps from the video.
   - **Writing Frames (`out.write()`)**: Adds individual frames to the video file.
   - **Reading Frames (`cap.read()`)**: Reads and retrieves frames from the video file or stream.
   - **Releasing Resources (`out.release()`, `cap.release()`)**: Properly closes and releases resources associated with video capture and writing.
