# Image Handling and Pixel Transformations Using OpenCV

## AIM

To write a Python program using OpenCV to read and display an image, draw shapes and text, convert between color spaces, access and modify pixel values, resize and crop an image, flip an image horizontally and vertically, and save the final modified image.

## Software Required

- Python 3
- OpenCV (`cv2`)
- Matplotlib
- Jupyter Notebook

## ALGORITHM

1. Import OpenCV and Matplotlib libraries.
2. Read the image using OpenCV and display it using Matplotlib.
3. Draw a line, circle, rectangle, and text on the image.
4. Convert the image into HSV, grayscale, and YCrCb color spaces.
5. Convert the HSV image back to RGB and display the images.
6. Access pixel values and modify pixels by assigning white color.
7. Resize the image to half its original width and height.
8. Crop a region of interest (ROI) from the image.
9. Flip the image horizontally and vertically.
10. Save the modified image using OpenCV.

## PROGRAM

### 1. Read and Display an Image

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread('myfoto.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```

### 2. Draw a Line

```python
image = cv2.imread('myfoto.jpg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
height, width = img_rgb.shape[:2]

line_img = cv2.line(img_rgb.copy(), (0, 0), (width - 1, height - 1), (255, 0, 0), 2)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()
```

### 3. Draw a Circle

```python
image = cv2.imread('myfoto.jpg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
height, width = img_rgb.shape[:2]

circle_img = cv2.circle(img_rgb.copy(), (width // 2, height // 2), 150, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()
```

### 4. Draw a Rectangle

```python
image = cv2.imread('myfoto.jpg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
height, width = img_rgb.shape[:2]

rectangle_img = cv2.rectangle(img_rgb.copy(), (0, 0), (width - 1, height - 1), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()
```

### 5. Add Text to the Image

```python
image = cv2.imread('myfoto.jpg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(
    img_rgb.copy(),
    "Raha Priya Dharshini M",
    (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX,
    1,
    (155, 118, 255),
    2
)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()
```

### 6. Convert Between Color Spaces

```python
image = cv2.imread('myfoto.jpg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
plt.show()

image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()

image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

### 7. Access and Modify Pixel Values

```python
image = cv2.imread('myfoto.jpg')

print("Pixel value at (100, 100):", image[100, 100])

image[200, 200] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Image with Modified Pixel")
plt.axis("off")
plt.show()
```

### 8. Modify a Region of Pixels

```python
image = cv2.imread('myfoto.jpg')

image[200:500, 200:500] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Image with White Block")
plt.axis("off")
plt.show()
```

### 9. Resize the Image

```python
image = cv2.imread('myfoto.jpg')
height, width = image.shape[:2]

resized_image = cv2.resize(image, (width // 2, height // 2))
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

print("Resized image dimensions:", resized_image_rgb.shape)

plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

### 10. Crop a Region of Interest (ROI)

```python
image = cv2.imread('myfoto.jpg')

roi = image[50:350, 50:350]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

### 11. Flip the Image Horizontally and Vertically

```python
image = cv2.imread('myfoto.jpg')

flipped_horizontally = cv2.flip(image, 1)
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()

flipped_vertically = cv2.flip(image, 0)
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

### 12. Save the Modified Image

```python
image = cv2.imread('myfoto.jpg')
image[200:500, 200:500] = [255, 255, 255]

cv2.imwrite('final_modified_image.jpg', image)
```

## OUTPUT

### 1. Original Image

<img width="1131" height="652" alt="Screenshot 2026-10-23 140916" src="https://github.com/user-attachments/assets/a577a2df-ef42-4da3-b51d-703e269cc4eb" />


### 2. Image with Line, Circle, Rectangle, and Text

<img width="768" height="516" alt="Screenshot 2026-10-23 140940" src="https://github.com/user-attachments/assets/7645f817-5a2f-42e1-a48b-e8e860d5f804" />

<img width="906" height="521" alt="Screenshot 2026-10-23 140947" src="https://github.com/user-attachments/assets/f2c17442-ec1f-4e62-917a-e3452692e7af" />

<img width="960" height="507" alt="Screenshot 2026-10-23 140957" src="https://github.com/user-attachments/assets/630608ce-de54-4cbf-82e8-f945cdf5fe8f" />

<img width="863" height="508" alt="Screenshot 2026-10-23 141009" src="https://github.com/user-attachments/assets/7cdfd662-5c81-4230-a3e1-976aaab58b8f" />


### 3. Color Space Conversion

<img width="946" height="527" alt="Screenshot 2026-10-23 141025" src="https://github.com/user-attachments/assets/eacefea1-b0c3-4a85-af06-d99173af3cea" />


### 4. Pixel Modification
<img width="946" height="527" alt="Screenshot 2026-10-23 141025" src="https://github.com/user-attachments/assets/2b8b1e6c-3a49-4939-a03c-29d31dd5050f" />

<img width="911" height="516" alt="Screenshot 2026-10-23 141031" src="https://github.com/user-attachments/assets/6eb957f4-2298-42e0-9b62-0179df464412" />

<img width="937" height="522" alt="Screenshot 2026-10-23 141038" src="https://github.com/user-attachments/assets/d2dd344b-68f9-4ca0-9306-f48506ec78c6" />

### 5. Resized Image

<img width="850" height="521" alt="Screenshot 2026-10-23 141102" src="https://github.com/user-attachments/assets/37ebeb3a-2fa7-4210-b799-c8174b18bfbf" />


### 6. Cropped Image

<img width="960" height="508" alt="Screenshot 2026-10-23 141110" src="https://github.com/user-attachments/assets/60a255cc-44a7-4be4-965b-9f0fa9c9c04d" />


### 7. Horizontally and Vertically Flipped Images

<img width="895" height="502" alt="Screenshot 2026-10-23 141117" src="https://github.com/user-attachments/assets/ea81ed00-a587-4920-9a76-c409fe0f6309" />

<img width="930" height="512" alt="Screenshot 2026-10-23 141124" src="https://github.com/user-attachments/assets/62a2ea63-4bf7-4287-bd7b-28024c256604" />



## RESULT

Thus, image handling and pixel transformations were performed using OpenCV, including image reading, display, drawing shapes and text, color space conversion, pixel modification, resizing, cropping, flipping, and saving the modified image successfully.
