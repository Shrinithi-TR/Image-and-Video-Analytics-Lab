import cv2
import matplotlib.pyplot as plt

# Read image in grayscale
img = cv2.imread("grayscale.png", 0)

if img is None:
    print("Image not found")
    exit()
g1 = cv2.pyrDown(img)
g2 = cv2.pyrDown(g1)
g3 = cv2.pyrDown(g2)

# Display results
plt.figure(figsize=(10,6))

plt.subplot(2,2,1)
plt.imshow(img, cmap='gray')
plt.title("Original")
plt.axis('off')

plt.subplot(2,2,2)
plt.imshow(g1, cmap='gray')
plt.title("Level 1")
plt.axis('off')

plt.subplot(2,2,3)
plt.imshow(g2, cmap='gray')
plt.title("Level 2")
plt.axis('off')

plt.subplot(2,2,4)
plt.imshow(g3, cmap='gray')
plt.title("Level 3")
plt.axis('off')

plt.show()



"C:\Users\CSE-DEPT\Pictures\Screenshots\Screenshot 2026-02-18 093411.png"
  
