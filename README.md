# Exp 6 - edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** Deepak K R  
- **Register No:** 212225040057  

---
## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('Tuatara.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```

### 1. Sobel Edge Detector

```python
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  # Sobel in x direction
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  # Sobel in y direction
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  # Combine both directions
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```

### 2. Prewitt Edge Detector

```py
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Define Prewitt kernels
kernel_prewitt_x = np.array([[-1, 0, 1], 
                             [-1, 0, 1], 
                             [-1, 0, 1]], dtype=np.float32)
                             
kernel_prewitt_y = np.array([[-1, -1, -1], 
                             [ 0,  0,  0], 
                             [ 1,  1,  1]], dtype=np.float32)

# Apply filters using cv2.filter2D
prewitt_x = cv2.filter2D(gray_image, cv2.CV_64F, kernel_prewitt_x)
prewitt_y = cv2.filter2D(gray_image, cv2.CV_64F, kernel_prewitt_y)

# Combine both directions
prewitt_combined = cv2.magnitude(prewitt_x, prewitt_y)

plt.imshow(prewitt_combined, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
```

### 3. Roberts Edge Detector
```py
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Define Roberts Cross kernels
kernel_roberts_x = np.array([[ 1,  0], 
                             [ 0, -1]], dtype=np.float32)
                             
kernel_roberts_y = np.array([[ 0,  1], 
                             [-1,  0]], dtype=np.float32)

# Apply filters using cv2.filter2D
roberts_x = cv2.filter2D(gray_image, cv2.CV_64F, kernel_roberts_x)
roberts_y = cv2.filter2D(gray_image, cv2.CV_64F, kernel_roberts_y)

# Combine both directions
roberts_combined = cv2.magnitude(roberts_x, roberts_y)

plt.imshow(roberts_combined, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
```

### 4. Laplacian Edge Detector
```py
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
```

### 5. Canny Edge Detector
```py
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off') 
```

## Output

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.