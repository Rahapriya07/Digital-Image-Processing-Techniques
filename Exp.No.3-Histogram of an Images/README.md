# Exp. No.3: Histogram of an Image
# Name:Raha Priya Dharshini M
# Reg.no:212224240124



## Aim
To study image histograms and perform histogram equalization on grayscale and color images using Python and OpenCV.

## Software Requirements
- Python
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Procedure

### A. Histogram Equalization for Grayscale Images
1. Import the required Python libraries.
2. Read the input image `myfoto.jpg` in grayscale mode.
3. Display the original grayscale image.
4. Calculate and plot the histogram of the original image using `plt.hist()`.
5. Apply histogram equalization using `cv2.equalizeHist()`.
6. Display the equalized image and its histogram.
7. Compare the original and equalized results.

### B. Histogram Equalization for Color Images
1. Read the input image `myfoto.jpg` in color mode.
2. Convert the image from BGR to HSV color space.
3. Apply histogram equalization to the Value (brightness) channel.
4. Convert the resulting image back from HSV to BGR color space.
5. Display the original and equalized color images.
6. Plot the histograms and compare the results.

## Code
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('myfoto.jpg', cv2.IMREAD_GRAYSCALE)

if img is None:
    raise FileNotFoundError("myfoto.jpg not found")

plt.imshow(img, cmap='gray')
plt.title('Original Grayscale Image')
plt.show()

plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Grayscale Histogram')
plt.show()

img_eq = cv2.equalizeHist(img)

plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Grayscale Histogram')
plt.show()

plt.imshow(img_eq, cmap='gray')
plt.title('Equalized Grayscale Image')
plt.show()

img = cv2.imread('myfoto.jpg', cv2.IMREAD_COLOR)

if img is None:
    raise FileNotFoundError("myfoto.jpg not found")

img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])
img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)

plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Color Image')
plt.show()

plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Color Image Histogram')
plt.show()

plt.figure(figsize=(20, 10))
plt.subplot(221)
plt.imshow(img[:, :, ::-1])
plt.title('Original Color Image')

plt.subplot(222)
plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Color Image')
plt.show()

plt.figure(figsize=(15, 4))
plt.subplot(121)
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Color Image Histogram')

plt.subplot(122)
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Color Image Histogram')
plt.show()
```

## Output Screenshots

### 1. Original Grayscale Image
<img width="1367" height="552" alt="image" src="https://github.com/user-attachments/assets/25437eba-fea1-41f0-9eb1-c29267a82c47" />


### 2. Original Grayscale Histogram
<img width="1357" height="550" alt="image" src="https://github.com/user-attachments/assets/b0aaf2cf-01a3-4db5-a48c-8c9b929f33d5" />


### 3. Equalized Grayscale Image
<img width="1365" height="545" alt="image" src="https://github.com/user-attachments/assets/8dc720c0-7111-4159-8b71-7f5e57e48be0" />


### 4. Equalized Grayscale Histogram
<img width="1362" height="578" alt="image" src="https://github.com/user-attachments/assets/d082da32-99da-4a94-951e-ebf9008322fa" />


### 5. Original and Equalized Color Images
<img width="1366" height="480" alt="image" src="https://github.com/user-attachments/assets/cfa126d2-e4f7-478b-a92c-faec1b6da952" />


### 6. Original and Equalized Color Histograms
<img width="1366" height="445" alt="image" src="https://github.com/user-attachments/assets/146004af-6f58-4a98-a23a-9dcd2ec57c2c" />


## Result
Thus, histogram equalization was performed on grayscale and color images using OpenCV. The original and equalized images and their histograms were displayed for comparison.
