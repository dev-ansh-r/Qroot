# 5. Walk without the joystick

`robot/jero.sh` waits for the pad, so start the walk directly with `--no-xbox` and drive it from the
keyboard over the link. **In the air first, then on the floor.**

**Terminal A: the walk**

```bash
python robot/jero_walk.py --board other --imu mpu6050 --serial-port /dev/jero-servo --no-xbox
```

Check first whether it starts paused:

```bash
grep start_paused ~/duck_config.json
```

With `false` it starts stepping in place as soon as it's up. With `true` it waits for `p` in terminal B.

**Terminal B: keyboard driving**

```bash
python brain/teleop.py 127.0.0.1
```

| Key | Action |
|---|---|
| `p` | pause / resume |
| `w` / `s` | forward / back (each press adds speed) |
| `a` / `d` | turn left / right |
| `q` / `e` | sidestep left / right |
| `i` / `k`, `j` / `l` | head up / down, left / right |
| space | stop (zero speed, keeps stepping) |
| `x` | E-STOP (pause) |
| Ctrl+C | quit teleop (the walk keeps running) |

Ctrl+C in terminal A stops the walk and releases the servos: hold the robot.

This path skips the real-time priority boost `jero.sh` gives the walk. That's fine for a test, but use
step 6 for the demo.
