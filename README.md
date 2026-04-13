"Homework1"
import cv2
import numpy as np

ix, iy = -1, -1
ex, ey = -1, -1
drawing = False
mode = True 

def nothing(x):
    pass

def draw_rect(event, x, y, flags, param):
    global ix, iy, ex, ey, drawing

    if event == cv2.EVENT_LBUTTONDOWN:
        drawing = True
        ix, iy = x, y
        ex, ey = x, y # 초기화

    elif event == cv2.EVENT_MOUSEMOVE:
        if drawing:
            ex, ey = x, y

    elif event == cv2.EVENT_LBUTTONUP:
        drawing = False
        ex, ey = x, y
        
img = cv2.imread('mountain.jpg')
if img is None:
    img = np.zeros((400, 600, 3), np.uint8)
    print("이미지 파일을 찾을 수 없어 빈 화면으로 대체합니다.")

cv2.namedWindow('image')
cv2.createTrackbar('R', 'image', 0, 255, nothing)
cv2.createTrackbar('G', 'image', 0, 255, nothing)
cv2.createTrackbar('B', 'image', 0, 255, nothing)

switch = '0:OFF\n1:ON'
cv2.createTrackbar(switch, 'image', 0, 1, nothing)

cv2.setMouseCallback('image', draw_rect)

while True:
    clone = img.copy()

    r = cv2.getTrackbarPos('R', 'image')
    g = cv2.getTrackbarPos('G', 'image')
    b = cv2.getTrackbarPos('B', 'image')
    s = cv2.getTrackbarPos(switch, 'image')

    x1, x2 = min(ix, ex), max(ix, ex)
    y1, y2 = min(iy, ey), max(iy, ey)

    if s == 1 and x1 != -1:
        if x1 != x2 and y1 != y2:
            clone[y1:y2, x1:x2] = [b, g, r]
            
            cv2.rectangle(clone, (x1, y1), (x2, y2), (0, 255, 0), 1)

    info = f"Mouse: ({ix},{iy}) - ({ex},{ey}) | RGB: ({r},{g},{b}) | Switch: {s}"
    cv2.putText(clone, info, (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 0.6, (255, 255, 255), 1)

    cv2.imshow('image', clone)

    k = cv2.waitKey(1) & 0xFF
    if k == 27:
        break

cv2.destroyAllWindows()
      


"Homework2"





"Homework3"

![dsu4](https://github.com/user-attachments/assets/4395351c-ac60-45a3-81e3-325fd36c8d99)
<img width="1022" height="794" alt="homework3 실행화면" src="https://github.com/user-attachments/assets/762c8885-4519-4ff2-a1a1-0be003241714" />

import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('dsu4.jpg')
rows,cols = img.shape[:2]
pts1 = np.float32([[324, 335], [546, 310], [550, 620]])
pts2 = np.float32([[100, 250], [500, 250], [500, 650]])
M = cv2.getAffineTransform(pts1, pts2)
dst = cv2.warpAffine(img, M, (cols, rows))
cv2.imshow('Affine Transform',dst)
cv2.waitKey(0)
cv2.destroyAllWindows()


"Homework4"





"Homework5"





