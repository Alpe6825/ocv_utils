# OCV_Utils 




## Install

```bash
pip3 install git+https://github.com/Alpe6825/ocv_utils
```

## Utils

### Image I/O

#### Loading

Load image and convert it to a certain channel type definition. Supported types `rgb`, `rgba`, `gray`

```python
from ocv_utils import load_image

img = load_image("my_image.png", channels="rgba")
```

### Video I/O

#### Reading
```python
from ocv_utils import VideoReader

video = VideoReader("video.mp4")

# cv2 like
while True:
    ret, frame = video.read()
    if not ret:
        break

# Or read certain frame
ret, frame = video.read(frame_id=42)
```



### Window
```python
import numpy as np
from ocv_utils import Window

window = Window(delay=0)
window.add_trackbar("x", 1, 255)
window.add_key_action(ord('h'), lambda: print("Hello World!"))

img1 = np.zeros((256, 256), dtype=np.uint8)
img2 = np.random.random((256, 256, 3))

trackbar_values = window.imshow([img1, img2])
print("Trackbar Values:", trackbar_values) # Trackbar Values: {'x': 1}

```