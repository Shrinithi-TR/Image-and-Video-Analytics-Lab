import cv2
import matplotlib.pyplot as plt

# Load Haar Cascade classifier
cascade = cv2.CascadeClassifier(cv2.data.haarcascades +
                                "haarcascade_frontalface_default.xml")

# Read image
img = cv2.imread("face.jpg")

if img is None:
    print("Image not found")
    exit()

# Convert to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Detect faces
faces = cascade.detectMultiScale(gray, scaleFactor=1.3, minNeighbors=5)

# Draw rectangles
for (x, y, w, h) in faces:
    cv2.rectangle(img, (x, y), (x+w, y+h), (0, 255, 0), 2)

# Display result
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Object Detection and Recognition")
plt.axis('off')
plt.show()

print("Object detection completed successfully.")

output:
<img width="467" height="245" alt="image" src="https://github.com/user-attachments/assets/606a4a02-03eb-4205-a2ef-4ba5a29ed664" />

