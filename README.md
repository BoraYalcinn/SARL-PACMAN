# SARL-PACMAN

An agentic PacMan game written in [SARL](http://www.sarl.io), made for my labwork at UTBM (IA51).

The maze, the pills and the bodies live in an environment agent that collects the agents' influences
and sends back a filtered perception every simulation step. PacMan is driven by the keyboard through
the Swing UI, while each ghost is an autonomous agent that decides its own move from what it perceives.

## Ghost behaviour

Each ghost reacts to its `Perception` event:

- chases PacMan by moving on the axis that reduces the distance, when that direction is free;
- flees in the opposite direction while PacMan is in super mode;
- otherwise wanders randomly, avoiding U-turns and other ghosts;
- walls and ghost bodies are treated as blocked cells.

## Project layout

```
src/main/sarl/fr/utbm/info/ia51/
├── framework/                     # generic situated multi-agent framework
└── labworks/pacman/
    ├── PacManBoot.sarl            # boot agent (world size, number of ghosts, perception range)
    ├── players/Players.sarl       # Ghost agent behaviour
    ├── environment/               # maze model, bodies, environment agent
    └── ui/PacManGUI.sarl          # Swing user interface
```

## Requirements

- Java 21
- SARL / Janus 0.15.1 runtime (the SARL Eclipse IDE ships with it)
- Maven 3.9+

## Build & run

```bash
mvn clean package
```

Then launch the agent `fr.utbm.info.ia51.labworks.pacman.PacManBoot` on the Janus runtime
(in the SARL Eclipse IDE: *Run As → SARL Application*).

Use the arrow keys to move PacMan. Eat all the pills to win; eat a super pill to hunt the ghosts.

## License

This project is released under the MIT license (see `LICENSE`). The UTBM framework and lab sources
keep their original LGPL v2.1 headers.
