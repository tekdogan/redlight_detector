# redlight_detector

This is an OpenCV project which aims to filter the red color in a given png file.

## Tutorial

Firstly we need to import the necessary packages. Importing numpy for numerical processing, argparse for parsing our command line arguments and cv2 for OpenCV operations.

```python
import numpy as np
import cv2, argparse
```
Lines below are handling the command line arguments, where we will be fetching our png file.

```python
ap = argparse.ArgumentParser()
ap.add_argument("-i", "--image")
args = vars(ap.parse_args())

img = cv2.imread(args["image"])
```

Now we have to define the thresholds (or boundaries) for the red color. Since OpenCV represents images as NumPy arrays in reverse order, instead of RGB, we can think of our array as BGR (Blue, Green, Red).

Blue and Green colors must be between [0,25], since we don't want their effect on image too much.
Red color may be any number since we want to get all the tones of red. ([0,255])

```python
lower = np.array([0, 0, 0], dtype = "uint8")
upper = np.array([25, 25, 255], dtype = "uint8")
```

And we implement our mask by using these boundaries, then output a resulting image by filtering (bitwise AND) operation.

```python
mask = cv2.inRange(img, lower, upper)

output = cv2.bitwise_and(img, img, mask=mask)
```


