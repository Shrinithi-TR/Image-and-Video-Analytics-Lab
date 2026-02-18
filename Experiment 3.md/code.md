import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load image
img = cv2.imread("grayscale.png")

if img is None:
    print("Image not found")
    exit()

rows, cols = img.shape[:2]

# 1. Translation
M_translation = np.float32([[1, 0, 50], [0, 1, 30]])
translated = cv2.warpAffine(img, M_translation, (cols, rows))

# 2. Rotation
M_rotation = cv2.getRotationMatrix2D((cols/2, rows/2), 45, 1)
rotated = cv2.warpAffine(img, M_rotation, (cols, rows))

# 3. Scaling
scaled = cv2.resize(img, None, fx=0.5, fy=0.5)

# 4. Reflection (Flip)
flipped = cv2.flip(img, 1)  # 1 = horizontal flip

# Display results
plt.figure(figsize=(10,8))

plt.subplot(2,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis('off')

plt.subplot(2,3,2)
plt.imshow(cv2.cvtColor(translated, cv2.COLOR_BGR2RGB))
plt.title("Translated")
plt.axis('off')

plt.subplot(2,3,3)
plt.imshow(cv2.cvtColor(rotated, cv2.COLOR_BGR2RGB))
plt.title("Rotated")
plt.axis('off')

plt.subplot(2,3,4)
plt.imshow(cv2.cvtColor(scaled, cv2.COLOR_BGR2RGB))
plt.title("Scaled")
plt.axis('off')

plt.subplot(2,3,5)
plt.imshow(cv2.cvtColor(flipped, cv2.COLOR_BGR2RGB))
plt.title("Flipped")
plt.axis('off')

plt.tight_layout()
plt.show()

print("Geometric transformations applied successfully.")


output:
<img width="513" height="588" alt="image" src="https://github.com/user-attachments/assets/c7e98825-2230-4f41-a1ef-38d30bfb780a" />
<img width="473" height="662" alt="image" src="https://github.com/user-attachments/assets/29434cc9-717b-40d1-b02d-6ab2a6501992" />
<img width="477" height="342" alt="image" src="https://github.com/user-attachments/assets/eff42daf-7aa6-46f7-9a72-39e6b061d428" />


