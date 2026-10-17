# 1. Pose

Servo battery on, Pico plugged in, robot held or on a stand (feet off the ground).

```bash
python tools/pose.py zero --port /dev/jero-servo   # every joint at 0 (servo 2048): horn check
python tools/pose.py init --port /dev/jero-servo   # the standing start pose the walk uses
```

- Moves smoothly over 3 s (`--seconds 5` for slower), then holds.
- **Enter releases torque**: support the robot first. Ctrl+C also releases.

If it fails with `bridge reported a failed transaction for IDs [...]` for all 14 servos, the Pico
answered but the servos didn't: the servo battery is off or still powering up. Switch it on, wait a
second, run again.
