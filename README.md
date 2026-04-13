"Homework1"

      

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





