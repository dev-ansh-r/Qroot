# 2. Check the servos

Servo battery on. Nothing moves.

```bash
python tools/bus_test.py --port /dev/jero-servo              # reads all 14 servos 300 times
python tools/bus_test.py --port /dev/jero-servo --rounds 50  # quick version
```

Whole robot in one go (servos, IMU, policy timing, pad, camera, dashboard, speaker, mic, voice,
network). Prints PASS / WARN / FAIL per line, nothing moves:

```bash
tools/rb3_dryrun.sh
```

Stop the walk first: the bus test is skipped while `jero.sh` holds the servo port.

| Message | Fix |
|---|---|
| `Pico not on USB` | replug the Pico's USB cable; `lsusb \| grep 2e8a` should list it |
| `servos not answering` | servo battery off |
| `/dev/jero-servo in use` | the walk is running: Ctrl+C it first |
