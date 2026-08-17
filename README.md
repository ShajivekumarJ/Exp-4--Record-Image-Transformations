# Geometric Transformations Using OpenCV
# DEVELOPED BY : SHAJIVE KUMAR J 
# REG NO : 212225230258
# Aim
To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

Image Translation
Image Scaling (Resizing)
Image Shearing
Image Reflection (Flipping)
Image Rotation

# Software Used
Anaconda – Python 3.7
Jupyter Notebook / VS Code
OpenCV (cv2)
NumPy
Matplotlib
## Algorithm
# Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

# Step 2:
Read the input image in color mode.

# Step 3: Image Translation
Create a translation matrix to shift the image
Move the image 50 pixels to the right and 80 pixels down
Apply transformation using cv2.warpAffine()
Display original and translated images
# Step 4: Image Scaling
Resize the image to 0.5× (downscale)
Resize the image to 2× (upscale)
Use cv2.resize()
Display original, downscaled, and upscaled images
# Step 5: Image Shearing
Create transformation matrices for:
Horizontal shearing
Vertical shearing
Apply transformations using cv2.warpAffine()
Display original and sheared images
# Step 6: Image Reflection
Perform flipping using cv2.flip():
Horizontal reflection
Vertical reflection
Both axes
Display all reflected images
# Step 7: Image Rotation
Create rotation matrices for:
45° rotation
90° rotation
Use cv2.getRotationMatrix2D() and cv2.warpAffine()
Display original and rotated images
# Program
```
Developed By: 
Name: SHAJIVE KUMAR J 

Register No:212225230258

```
```



# Geometric Transformations Using OpenCV

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
img = cv2.imread("image.jpg")

# Convert BGR to RGB for display
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

rows, cols = img.shape[:2]
```
```

# -----------------------------
# 1. Image Translation
# -----------------------------
M_translate = np.float32([[1, 0, 50],
                          [0, 1, 80]])

translated = cv2.warpAffine(img_rgb, M_translate, (cols, rows))

plt.figure(figsize=(8,4))
plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated)
plt.title("Translated")
plt.axis("off")
plt.show()
```
```

# -----------------------------
# 2. Image Scaling
# -----------------------------
downscaled = cv2.resize(img_rgb, None, fx=0.5, fy=0.5,
                        interpolation=cv2.INTER_AREA)

upscaled = cv2.resize(img_rgb, None, fx=2, fy=2,
                      interpolation=cv2.INTER_LINEAR)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled)
plt.title("Downscaled (0.5x)")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled)
plt.title("Upscaled (2x)")
plt.axis("off")
plt.show()
```
```

# -----------------------------
# 3. Image Shearing
# -----------------------------
M_horizontal = np.float32([[1, 0.5, 0],
                           [0, 1, 0]])

horizontal_shear = cv2.warpAffine(
    img_rgb, M_horizontal,
    (int(cols + cols*0.5), rows)
)

M_vertical = np.float32([[1, 0, 0],
                         [0.5, 1, 0]])

vertical_shear = cv2.warpAffine(
    img_rgb, M_vertical,
    (cols, int(rows + rows*0.5))
)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal_shear)
plt.title("Horizontal Shear")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical_shear)
plt.title("Vertical Shear")
plt.axis("off")
plt.show()
```
```

# -----------------------------
# 4. Image Reflection
# -----------------------------
horizontal_flip = cv2.flip(img_rgb, 1)
vertical_flip = cv2.flip(img_rgb, 0)
both_flip = cv2.flip(img_rgb, -1)

plt.figure(figsize=(12,4))

plt.subplot(1,4,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,4,2)
plt.imshow(horizontal_flip)
plt.title("Horizontal Flip")
plt.axis("off")

plt.subplot(1,4,3)
plt.imshow(vertical_flip)
plt.title("Vertical Flip")
plt.axis("off")

plt.subplot(1,4,4)
plt.imshow(both_flip)
plt.title("Both Axes")
plt.axis("off")
plt.show()
```
```

# -----------------------------
# 5. Image Rotation
# -----------------------------
center = (cols // 2, rows // 2)

M45 = cv2.getRotationMatrix2D(center, 45, 1)
rotate45 = cv2.warpAffine(img_rgb, M45, (cols, rows))

M90 = cv2.getRotationMatrix2D(center, 90, 1)
rotate90 = cv2.warpAffine(img_rgb, M90, (cols, rows))

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotate45)
plt.title("45° Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotate90)
plt.title("90° Rotation")
plt.axis("off")
plt.show()
```
# Output :

# Image Translation
Original image is displayed
Translated image (shifted right and down) is displayed

<img width="696" height="257" alt="image" src="https://github.com/user-attachments/assets/60ecc3f7-0b86-4c88-9924-b7aba25c7ca4" />



# Image Scaling
Original image is displayed
Downscaled image (0.5×) is displayed
Upscaled image (2×) is displayed

<img width="1005" height="245" alt="image" src="https://github.com/user-attachments/assets/2e251772-8785-4811-b895-cea2b5db154f" />


# Image Shearing
Original image is displayed
Horizontally sheared image is displayed
Vertically sheared image is displayed

<img width="1082" height="355" alt="image" src="https://github.com/user-attachments/assets/8da867c8-6401-41c2-b3a3-4ff9779a4878" />


# Image Reflection
Original image is displayed
Horizontally flipped image is displayed
Vertically flipped image is displayed
Both-axis flipped image is displayed

<img width="1107" height="202" alt="image" src="https://github.com/user-attachments/assets/31aad349-73f5-4b19-861c-b2a1e44d5ad2" />


# Image Rotation
Original image is displayed
45° rotated image is displayed
90° rotated image is displayed

<img width="1081" height="255" alt="image" src="https://github.com/user-attachments/assets/f9ed6961-7c8f-4308-b224-0f687762f7e1" />


# Result
Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
