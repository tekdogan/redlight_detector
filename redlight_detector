import numpy as np
import cv2, argparse

ap = argparse.ArgumentParser()
ap.add_argument("-i", "--image")
args = vars(ap.parse_args())

img = cv2.imread(args["image"])

lower = np.array([0, 0, 0], dtype = "uint8")
upper = np.array([25, 25, 255], dtype = "uint8")

mask = cv2.inRange(img, lower, upper)

output = cv2.bitwise_and(img, img, mask=mask)

cv2.imshow("", np.hstack([img, output]))

cv2.waitKey(0)
