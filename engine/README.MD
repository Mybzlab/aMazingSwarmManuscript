This directory has the main simulation engine for testing cooperative transport in a maze setting.
Below there is a minimal example and an extended synopsis for using the engine.

**Minimal Example**
A minimal example for a 4x4 maze that can be quickly ran on a laptop is achieved using the following commands

  python main.py 4 --full-npz 4x4

  python src/render_final_frame.py data/4x4.npz

  python src/visualization.py data/4x4.npz 4x4.mp4

The first command runs a simulation of a 4x4 maze with standard parameters.
The second command generates the final frame showing the payload's trajectory from entry to final step and the location of the active particles in the final step.
The third command generates a video from the simulation data showing the progress of the payload and the motion of the particles.

**Extended Synopsis**
