# 4. Eyes and app (dashboard)

Two programs, each in its own terminal.

**Terminal A: the dashboard (camera, depth, Commands, Jero says, Path covered)**

```bash
~/.virtualenvs/jero-vision/bin/python ~/Jero/brain/eyes.py
```

Open `http://<rb3-address>:8080` on any laptop or phone on the same Wi-Fi (`hostname -I` gives the
address). Keys: F fullscreen, Esc closes the photo.

| Option | Use |
|---|---|
| `--follow` | head turns toward the nearest object (walk running and unpaused) |
| `--follow --dry-run` | only log the head commands |
| `--rotate 180` | camera mounted upside down |
| `--fps 30` | smoother, more CPU (default 15) |

Photos go to `~/jero-photos/`.

**Terminal B: the show controller (makes the Commands buttons speak and move)**

```bash
~/jero-speech/.venv/bin/python ~/Jero/brain/show.py --dry-run   # speaks + shows text, motions only logged
~/jero-speech/.venv/bin/python ~/Jero/brain/show.py             # for real: walk must be running (step 5 or 6)
```

Buttons: **Capture image** (3-2-1, "Say cheese!", photo pops up), **Say hi** (greeting + wave),
**Wanna see a dance?** (asks, waits, dances), **Stop**.

Say a line on the dashboard from any terminal:

```bash
~/jero-speech/.venv/bin/python ~/Jero/brain/show_api.py say "Hello there"
```

Play the cached show lines to check the speaker:

```bash
for f in ~/.cache/jero/show-tts/*.wav; do pw-play "$f"; sleep 0.4; done
```

Stop either program with Ctrl+C.
