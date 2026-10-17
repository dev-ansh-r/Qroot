# 6. Walk with the joystick (PS4 pad)

Press the pad's **PS** button. Check it's connected:

```bash
ls /dev/input/js0
python tools/pad_test.py        # optional: move the sticks, see what the walk receives (20 s)
```

Start the walk (it waits for the pad, finds the Pico, raises the walk's priority, logs to `~/jero-logs/`):

```bash
robot/jero.sh
```

| Pad | Action |
|---|---|
| Cross (X) | start / pause |
| left stick | walk forward / back / sideways |
| right stick | turn |
| L1 held | faster steps |
| Ctrl+C in the terminal | stop the walk, servos released: **hold the robot** |

**In the air first, then on the floor.** Pause with Cross before picking it up.

Re-pair if the pad won't connect (once):

```bash
bluetoothctl            # then: scan on / pair <MAC> / trust <MAC> / connect <MAC>
```
