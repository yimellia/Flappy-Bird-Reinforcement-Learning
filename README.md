# Flappy Bird Reinforcement Learning
Reinforcement Learning Project for Autonomous Flappy Bird Gameplay

---

## Dependencies

Install **pygame 1.9.6** package
Install **python 3.7**

---

## File Structure

- `src/bot.py` - This file contains the `Bot` class that applies the Q-Learning logic to the game.

- `src/flappy.py` - Main program file in python, play the game or train an agent to play the game

- `data/qvalues.json` - Q-table of state-actions in Q-Learning, start a new training by removing this file

- `data/hitmasks_data.pkl` - Mask data to detect crash in non-UI training mode

---

## How to Run

``` dos
python3 src/flappy.py [-h] [--fps FPS] [--episode EPISODE] [--ai]
                      [--train {normal,noui,replay}] [--resume]
                      [--max MAX] [--dump_hitmasks]
```

- `-h, --help` : Show usage formation
- `--fps FPS` : number of frames per second, default value:
  - User play or normal training mode with UI: `25`
  - Replay training mode: `20`
  - AI play mode: `60`
- `--episode EPISODE` : Training episode number, default: 10,000
- `--ai` : AI play mode
- `--train {normal,noui,replay}` : Training mode:
  - `normal` : Normal training mode with UI
  - `noui` : Training without UI, fastest training mode
  - `replay` : Training without UI, replay game with UI from last 50 steps once the bird crashes, it provides a visual way to check how bird crashed.
- `--resume` : Resume game from last 50 steps before crash, it's useful to correct flying trajectory for rare scenario. But it's 3x slower than normal mode. When in replay training mode, this option is enabled automatically.  
- `--max MAX` : Maxium score per episode, restart game if agent reach this score, default: 10,000,000
- `--dump_hitmasks` : dump hitmasks to file and exit

### Play game in user mode

``` dos
python3 src/flappy.py
```

### Train the agent bot without UI, play 1000 times

``` dos
python3 src/flappy.py --train noui --episode 1000
```

### Train the agent bot, replay last 50 steps before crash with UI, restart a new game when the bird reach 1000 scores

``` dos
python3 src/flappy.py --train replay --episode 1000 --max 1000
```

