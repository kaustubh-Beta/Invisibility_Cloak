# Invisibility cloak tutorial

This tutorial aims at explaining some key concepts of `image processing` using `opencv` with python.
We will try to understand each line of the [code](AR_invisibility_Cloak.py)

> ###### Note for someone using python for the first time:
> anything written after '#' will be treated as a comment. 
> it is a good practice to add comments in your code. 
> It makes the code easy to understand.


### Importing all the required libraries

```python
import cv2
import numpy as np
import time
```

### Extracting the static background frame
Now as explained in the [readme](README.md), We will replace the current frame pixels 
corresponding to the cloth with the background pixels to generate the effect of
an invisibility cloak. For this we need to store the frame of a static background.

```python
# Creating an VideoCapture object
# This will be used for image accusition later in the code.
cap = cv2.VideoCapture(0)

# We give some time for the camera to setup
time.sleep(3)

background=0
for i in range(30):
	ret,background = cap.read()
```
>cap.read() method enables us to capture latest frame(stored in variable `background`) with the camera
>and it also returns a boolean (True/False stored in `ret`). If frame is read correctly, it will be True. 
>So you can check end of the video by checking this return value.

###### Why capture background image using a for loop ?
As the background is static we can do with a single capture right ?
Well yes but the image captured is a bit dark compared to when 
multiple frames are captured. 
Hence capturing multiple images of static background with a for loop
did the trick for me.


### 
