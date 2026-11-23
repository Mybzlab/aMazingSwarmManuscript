The repository holds the results (A) and source code (B) of the numerical engine simulating Force-Aligning Active Brownian Particles (FAABP) pushing a payload in a maze environment.

* (A) The results are found in figures directory and associated with the figures in the mansucript.
* (B) The simulation core is found in src and includes:
    - Numerical engine simulating FAABPs with control over particles radius, self-propulsion speed, curvity, and persistence length
    - Occlusion based transport
    - Communication and score relaying
    - Maze generation
    - Maze solving using a swarm 
    - Video and figure rendering scripts


**References**
  1.   Arbel, Eden, Luco Buise, Charlotte van Waes, Naomi Oppenheimer, Yoav Lahini, and Matan Yah Ben Zion.
       “A Mechanical Route for Cooperative Transport in Autonomous Robotic Swarms.”
       Nature Communications 16, no. 1 (2025): 7519.
       https://doi.org/10.1038/s41467-025-61896-7.
  2.   Mathias Casiulis, Eden Arbel, Charlotte van Waes, Yoav Lahini, Stefano Martiniani, Naomi Oppenheimer, and Matan Yah Ben Zion
       “A Geometric Condition for Robot-Swarm Cohesion and Cluster–Flock Transition.”
       Proceedings of the National Academy of Sciences 122, no. 37 (2025).
       https://doi.org/10.1073/pnas.2502211122.


