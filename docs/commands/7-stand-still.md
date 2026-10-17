# 7. Stand still

The robot keeps balancing at zero speed (the policy stays on, so it can catch a nudge) while the head,
voice and dashboard do the show.

1. Start the walk: step 6 (`robot/jero.sh`, press Cross) or step 5 (without the pad).
2. Don't touch the sticks, or press space in teleop: speed is zero, Jero steps gently in place.

Head and expressions while standing (second terminal):

```bash
python brain/expressions.py curious           # looks around, question chirps (~10 s)
python brain/expressions.py glitch            # malfunction, power down, reboot, happy wiggle (~11 s)
python brain/expressions.py --loop            # both, with pauses: booth stand-by
python brain/expressions.py curious --dry-run # sounds + printed poses, robot untouched
```

Head follows your hand (dashboard terminal, instead of plain `eyes.py`):

```bash
~/.virtualenvs/jero-vision/bin/python ~/Jero/brain/eyes.py --follow
```

**Fully still (no stepping):** press **Cross** to pause. The robot holds its last joint positions with
torque on but **does not balance**, so keep a hand near it.

**Standing tilt correction** (once, if `rb3_dryrun.sh` says "no tilt correction"; walk stopped, robot on the floor):

```bash
python tools/imu_tilt.py --port /dev/jero-servo
```
