This directory has the main simulation engine for testing cooperative transport in a maze setting.
Below there is a minimal example and an extended synopsis for using the engine.

**Minimal Example**
A minimal example for a 4x4 maze that can be quickly ran on a laptop is achieved using the following commands

  `python main.py 4 --full-npz 4x4`

  `python src/render_final_frame.py data/4x4.npz`

  `python src/visualization.py data/4x4.npz 4x4.mp4`

The first command runs a simulation of a 4x4 maze with standard parameters.
The second command generates the final frame showing the payload's trajectory from entry to final step and the location of the active particles in the final step.
The third command generates a video from the simulation data showing the progress of the payload and the motion of the particles.

**Extended Synopsis**  

***Simulation***  
Run a simulation: main.py
Runs the swarm-and-payload maze simulation and saves an NPZ. A "light" NPZ is the default, with no video.

****Example:****

`python main.py 10 run_name --discrete-curvity --full-npz --corner-init --out-dir ./data/`

Positional arguments:

maze_grid_size: maze is C×C. Box size is 60 * C and particle count is 10 * G².
output_name: filename stem for the NPZ and mp4.
Flags:

--maze-seed N: Wilson maze seed (default 42).  
--n-particles N: override the default 10 * G² particles.  
--n-steps N: maximum number of simulation steps. The simulation automatically ends when the payload reaches the target.  
--save-interval N: steps between saved frames.  
--out-dir PATH: write outputs here, instead of the default ./data and ./visualizations.  
--corner-init: start the swarm densely around the payload in the start cell.  
--swarm-radius R: outer radius of that corner swarm.  
--video: save a full NPZ and render the built-in mp4.  
--full-npz: save a full NPZ without rendering the mp4.  
--score-interval N: steps between score updates (default 20).  
--async-update MIN MAX: each particle updates score every random MIN..MAX steps. This overrides --score-interval.  
--view-range R: particle observation range in absolute units (default 2.5 * cell).  
--nudge-strength X: radians per polarity nudge (default 0.01).  
--curvity-scale X: multiplier on the continuous curvity (default 1).  
--discrete-curvity: curvity is a hard ±1 switch on e·p.  
--vote-polarity: hard ±1 curvity from a majority vote of the lowest-score neighbours. This overrides --discrete-curvity.  
--diffusion-init-rule: Ignores neighbours that still hold the default score, and starts curvity at its max value (default: 1).  

***Render final frame***  
Render a final-frame PNG: src/render_final_frame.py   
Draws the last saved frame with particles, payload path, walls and goal. It works on "light" NPZs.  

****Example:****

`python src/render_final_frame.py data/run_name.npz --vmax 10 --no-inset`

Positional argument:  

data/run_name.npz: the npz file to render.  
Flags:  

--vmax N: score value where the colormap saturates.  
--no-inset: skip the payload zoom inset.  

***Render Video***  

Render an mp4 from a saved NPZ: src/visualization.py  
Turns a full NPZ into a video. The run must have used --video or --full-npz.  

****Example:****

`python src/visualization.py data/run_name.npz out.mp4 --fps 15 --vmax 10`

Positional arguments:

npz: full NPZ to render.  
output: mp4 path to write.  
Flags:  

--save-interval N: the SAVE_INTERVAL the NPZ was recorded with (default 100).  
--steps-per-frame N: simulation steps advanced per video frame (default 100).  
--fps N: video frame rate (default 15).  
--vmax N: upper end of the score colour range.  
--red-until-first-update: particles stay red until their first score update. Needs first_update_steps in the NPZ.  
--show-inset: add the payload zoom inset.  
--show-vectors: draw "polarity" arrows.  
