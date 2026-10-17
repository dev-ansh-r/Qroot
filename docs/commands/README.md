# Jero on the RB3 Gen 2: command sheets

Run the steps in order. Every command runs **on the RB3** (SSH in, or its own terminal) with the walk's
Python environment active:

```bash
source ~/.virtualenvs/open-duck-mini-runtime/bin/activate
cd ~/Jero
```

The camera and voice steps use their own environments; their commands give the full path.

1. [Pose](1-pose.md): servos to zero or the standing pose.
2. [Check the servos](2-servos.md): bus test and the whole-robot dry run.
3. [Check the camera](3-camera.md): RealSense on USB, frames arriving.
4. [Eyes and app](4-eyes-and-app.md): dashboard in the browser, show controller behind its buttons.
5. [Walk without the joystick](5-walk-no-pad.md): keyboard over the link.
6. [Walk with the joystick](6-walk-pad.md): PS4 pad.
7. [Stand still](7-stand-still.md): hold the pose, head moves and expressions only.

Emergency stop from any terminal on the RB3 (pauses the walk):

```bash
python tools/estop.py 127.0.0.1
```

Find the RB3's address (for SSH and the dashboard): `hostname -I`.
