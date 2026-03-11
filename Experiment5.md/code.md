Experiment 5
code:

import cv2
from google.colab.patches import cv2_imshow

# Load vehicle video
cap = cv2.VideoCapture("/content/vehilce.mp4")

ret, prev_frame = cap.read()
if not ret:
    print("Error loading video")
    exit()

prev_gray = cv2.cvtColor(prev_frame, cv2.COLOR_BGR2GRAY)

frame_count = 0

while True:
    ret, frame = cap.read()
    if not ret:
        break

    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    # Frame difference for motion analysis
    diff = cv2.absdiff(prev_gray, gray)

    # Threshold to highlight moving objects
    _, motion = cv2.threshold(diff, 25, 255, cv2.THRESH_BINARY)

    cv2_imshow(motion)

    prev_gray = gray

    frame_count += 1
    if frame_count >= 1:   # stop after 20 frames
        break

cap.release()

output:
<img width="1080" height="554" alt="image" src="https://github.com/user-attachments/assets/c0e2fde0-976b-4027-8806-96d8df837776" />


Test case 1:Human Walking

code:
import cv2
from google.colab.patches import cv2_imshow

cap = cv2.VideoCapture("/content/walking.mp4.mp4")

ret, frame1 = cap.read()

if not ret:
    print("Video not loaded")
    exit()

gray1 = cv2.cvtColor(frame1, cv2.COLOR_BGR2GRAY)
edges1 = cv2.Canny(gray1, 50, 150)

while True:
    ret, frame2 = cap.read()
    if not ret:
        break

    gray2 = cv2.cvtColor(frame2, cv2.COLOR_BGR2GRAY)
    edges2 = cv2.Canny(gray2, 50, 150)

    diff = cv2.absdiff(edges1, edges2)

    # Show output in Colab
    cv2_imshow(diff)

    edges1 = edges2

cap.release()

output:
<img width="1069" height="505" alt="image" src="https://github.com/user-attachments/assets/7845016f-971a-44ad-944c-e282b063a175" />

Test Case:2
Moving vehicle detection 

code:
import cv2
from google.colab.patches import cv2_imshow

cap = cv2.VideoCapture("/content/vehilce.mp4")

ret, frame1 = cap.read()

if not ret:
    print("Video not loaded. Check file path.")
    exit()

gray1 = cv2.cvtColor(frame1, cv2.COLOR_BGR2GRAY)
edges1 = cv2.Canny(gray1, 50, 150)

frame_count = 0

while True:
    ret, frame2 = cap.read()
    if not ret:
        break

    gray2 = cv2.cvtColor(frame2, cv2.COLOR_BGR2GRAY)
    edges2 = cv2.Canny(gray2, 50, 150)

    diff = cv2.absdiff(edges1, edges2)

    cv2_imshow(diff)

    edges1 = edges2

    frame_count += 1
    if frame_count >= 1:   # stop after 20 frames
        break

cap.release()

output:
<img width="1078" height="477" alt="image" src="https://github.com/user-attachments/assets/bda123d7-5c79-455e-a6ec-4c60ddfb6174" />
