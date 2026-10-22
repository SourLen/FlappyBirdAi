# Flappy Bird AI

An early project of mine, from around 2021, made while learning how AI works.
The idea was to explore neural networks and evolutionary algorithms by watching
birds learn to play Flappy Bird. The project is kept close to its original form
as a record of that learning process.

Built with Python, [Pygame](https://pypi.org/project/pygame/2.6.1/), and
[NEAT-Python](https://pypi.org/project/neat-python/0.92/).

## Run

Use Python 3.12 or 3.13 and run these commands from the project directory:

```sh
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python main.py
```

On Windows, create it with `py -3.12 -m venv .venv` and activate it with
`.venv\Scripts\activate` instead. Pygame 2.6.1 has no prebuilt packages for
Python 3.14; using it triggers a source build that requires SDL development files.
A Pygame window shows the birds training automatically. Close it to stop.
The dependency versions are pinned to keep the original NEAT configuration working.

## How it works

Each generation starts with 100 birds, each controlled by its own neural network.
The network receives the bird's height and its vertical distances to the two edges
of the next pipe opening. One output determines whether it flaps. Birds earn
fitness for surviving and passing pipes; NEAT evolves network weights and
structure across generations. Training runs for up to 50 generations and prints
the best genome at the end. A successful generation can run for a long time.

- `main.py`: the game and AI training loop.
- `config-feedforward.txt`: population and network settings.
- `imgs/`: game sprites.
- `flappy_bird_humen.py`: an unfinished human-play experiment, kept for context;
  it has no playable game loop.

## Credits

The implementation closely follows
[Tech With Tim's NEAT Flappy Bird tutorial](https://github.com/techwithtim/NEAT-Flappy-Bird).
