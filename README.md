Opening and Closing Operations Using OpenCV

## Aim
To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:
1. Morphological Opening
   
2. Morphological Closing
   
## Software Used
1. Anaconda
2. Python
3. Jupyter Notebook
4. OpenCV (cv2)
5. NumPy
6. Matplotlib
   
## Algorithm
**Step 1:**
Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2:**
Create a binary input image containing a foreground object, small foreground noise, and a small hole.

**Step 3:**
Display the original input image.

**Step 4:**
Create a suitable structuring element (kernel).

**Step 5:**
 Opening Operation
 
 Apply the Opening operation using the structuring element.
 
 Opening consists of Erosion followed by Dilation.
 
 Remove small foreground noise and isolated objects.
 
 Preserve the main structure of the foreground object.
 
 Display the opened image.

**Step 6: Closing Operation**
 Apply the Closing operation using the structuring element.
 
 Closing consists of Dilation followed by Erosion.
 
 Fill small holes and gaps within foreground objects.
 
 Improve the continuity of the foreground object.
 
 Display the closed image.

**Step 7:**
Compare the original, opened, and closed images to observe the effects of the morphological operations.

## Program
The complete Python program is implemented in the Jupyter Notebook:

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Create a black image
image = np.zeros((400, 400), dtype=np.uint8)

# Main white object
cv2.rectangle(image, (100, 100), (300, 300), 255, -1)

# Small white noise outside the object
for x, y in [(30, 30), (60, 50), (350, 40), (370, 70),
             (40, 350), (70, 370), (340, 350), (370, 370)]:
    cv2.circle(image, (x, y), 3, 255, -1)

# Large black hole inside the white object
cv2.circle(image, (200, 200), 20, 0, -1)

# Structuring element
kernel = np.ones((11, 11), np.uint8)

# Opening: erosion -> dilation
opening = cv2.morphologyEx(image, cv2.MORPH_OPEN, kernel)

# Closing: dilation -> erosion
closing = cv2.morphologyEx(image, cv2.MORPH_CLOSE, kernel)

# Display all results
plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(image, cmap="gray")
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(opening, cmap="gray")
plt.title("Opening")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(closing, cmap="gray")
plt.title("Closing")
plt.axis("off")

plt.tight_layout()
plt.show()
```

**Opening_Closing_OpenCV.ipynb**

**The program uses the following OpenCV functions:**
```
cv2.morphologyEx()
cv2.MORPH_OPEN
cv2.MORPH_CLOSE
cv2.imwrite()
```
## Developed By

## Name: ARUNACHALAM M 

## Register No: 212225230019

## Output

**Original Image**
 The original binary image is displayed.
 
 The image contains a main foreground object.
 
 Small white noise is present outside the object.
 
 A small black hole is present inside the object.
 
**Opening Operation**
 Small foreground noise is removed.
 
 The main foreground object is preserved.
 
 Opening performs erosion followed by dilation.
 
 The resulting image contains fewer unwanted foreground objects.
 
 **Closing Operation**
  Small holes and gaps in the foreground object are filled.
  
  The main object becomes more continuous.
  
  Closing performs dilation followed by erosion.
  
  The resulting image has improved object continuity.

  <img width="1537" height="524" alt="image" src="https://github.com/user-attachments/assets/5131b422-2293-46fd-9a6d-a9345af28ae1" />

## Applications
**Opening**
 Removal of small noise from binary images.
 
 Image preprocessing.
 
 Object separation.
 
 Improving image segmentation.
 
 Removing small unwanted foreground objects.
 
**Closing**
 Filling small holes in objects.
 
 Connecting nearby foreground regions.
 
 Removing small gaps.
 
 Improving object continuity.
 
 Enhancing segmented regions.
 
## Advantages
**Opening**
 Removes unwanted foreground noise.
 
 Preserves larger objects.
 
 Smooths object boundaries.
 
 Improves image segmentation.
 
**Closing**
 Fills small holes and gaps.
 
 Connects nearby regions.
 
 Preserves the overall object structure.
 
 Improves the continuity of segmented objects.
 
## Result:
Thus, the morphological operations Opening and Closing were successfully implemented using OpenCV. Opening was used to remove small foreground noise, while Closing was used to fill small holes and gaps and improve the continuity of the foreground object.
