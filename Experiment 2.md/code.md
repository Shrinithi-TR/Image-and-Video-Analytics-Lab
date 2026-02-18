import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load grayscale image
img = cv2.imread("grayscale.png", 0)

if img is None:
    print("Image not found")
    exit()

# Parameters
THRESHOLD = 10     # Homogeneity threshold
MIN_SIZE = 8       # Minimum block size

# Convert image to color for drawing rectangles
output = cv2.cvtColor(img, cv2.COLOR_GRAY2BGR)

def quadtree(image, x, y, w, h):
    region = image[y:y+h, x:x+w]

if w <= MIN_SIZE or h <= MIN_SIZE or np.std(region) < THRESHOLD:
        cv2.rectangle(output, (x, y), (x+w, y+h), (0, 255, 0), 1)
        return
    hw = w // 2
    hh = h // 2

   quadtree(image, x, y, hw, hh)               # Top-left
    quadtree(image, x+hw, y, hw, hh)            # Top-right
    quadtree(image, x, y+hh, hw, hh)            # Bottom-left
    quadtree(image, x+hw, y+hh, hw, hh)         # Bottom-right

# Start Quad Tree decomposition
height, width = img.shape
quadtree(img, 0, 0, width, height)

# Display result
plt.figure(figsize=(6,6))
plt.imshow(cv2.cvtColor(output, cv2.COLOR_BGR2RGB))
plt.title("Quad Tree Representation")
plt.axis('off')
plt.show()

print("Quad Tree representation completed successfully.")



output:

<img width="465" height="622" alt="image" src="https://github.com/user-attachments/assets/64cabc6a-6b94-4050-9b7c-97d21b27bba1" />

