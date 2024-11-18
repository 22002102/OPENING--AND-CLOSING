# OPENING--AND-CLOSING
### Aim
To implement Opening and Closing using Python and OpenCV.

### Software Required
1. Anaconda - Python 3.7
2. OpenCV
   
### Algorithm:
#### Step1:
Create a white image of specified size and add black text ("Sam") to it using cv2.putText.
#### Step2:
Add random salt-and-pepper noise to the image by setting random pixels to black or white.
#### Step3:
Create a smaller structuring element (kernel) of size 5x5 using np.ones().
### Step4:
Apply the Opening operation using cv2.morphologyEx() with erosion followed by dilation.
### Step5:
Apply the Closing operation using cv2.morphologyEx() with dilation followed by erosion.

## Program:
Import the necessary packages
```
import cv2
import numpy as np
from matplotlib import pyplot as plt
```
Create the Text using cv2.putText
```
img = np.ones((300, 600), dtype="uint8") * 255  # Create a white image
cv2.putText(img, 'SANJAY', (150, 150), cv2.FONT_HERSHEY_SIMPLEX, 3, (0, 0, 0), 5)  # Add black text 'Sam'
noise = np.random.rand(*img.shape)
img[noise < 0.05] = 0  # Random black pixels (salt)
img[noise > 0.95] = 255  # Random white pixels (pepper)
kernel = np.ones((5, 5), np.uint8)  # A smaller 5x5 square kernel
opening = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)
closing = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)
plt.figure(figsize=(12, 8))
```
Original image with noise
```
plt.subplot(1, 3, 1)
plt.title('Original Image with Noise')
plt.imshow(img, cmap='gray')
plt.axis('off')
```
Opening image
```
plt.subplot(1, 3, 2)
plt.title('Opening Operation')
plt.imshow(opening, cmap='gray')
plt.axis('off')
```
Closing image
```
plt.subplot(1, 3, 3)
plt.title('Closing Operation')
plt.imshow(closing, cmap='gray')
plt.axis('off')

plt.show()
```
## Output:
### Display the input Image
![image](https://github.com/user-attachments/assets/6e202899-3c15-4383-a7cb-1816226f0212)
### Display the result of Opening
![image](https://github.com/user-attachments/assets/d7d9ca58-5fb1-4096-9efc-0099feb67aeb)
### Display the result of Closing
![image](https://github.com/user-attachments/assets/50ad5a01-4c34-408c-a8f6-d8f0fcca9e10)

## Result
Thus the Opening and Closing operation is used in the image using python and OpenCV.
