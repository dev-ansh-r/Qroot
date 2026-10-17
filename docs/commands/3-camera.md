# 3. Check the camera

RealSense D455 on a USB 3 port.

```bash
lsusb | grep 8086:0b5c          # the camera is on USB
rs-enumerate-devices -s         # name, serial, USB type: want "3.2" (if librealsense tools are installed)
```

Quick frame test: the dashboard with the camera (step 4), and watch the fps in its header:

```bash
~/.virtualenvs/jero-vision/bin/python ~/Jero/brain/eyes.py
```

No camera at hand? Use a moving test scene to check the page:

```bash
~/.virtualenvs/jero-vision/bin/python ~/Jero/brain/eyes.py --fake
```

| Problem | Fix |
|---|---|
| not in `lsusb` | replug; use the USB-C cable that came with it |
| low fps, "USB 2" | it's on a USB 2 port or cable: move to a USB 3 port |
| image upside down | add `--rotate 180` |
