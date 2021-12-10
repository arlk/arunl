@def title = "Research Overview"

# Research

## Synthesis of Incremental Regions of Attraction
Formal methods in control design for nonlinear systems are often focused on the stabilization of an equilibrium. Modern robotics applications, however, require notions of stability to be defined when tracking reference trajectories. The idea behind an _incremental region of attraction_ is that as long as an attractive region can be defined around any trajectory within some operating regime then all initial conditions of the system that start within the region converge to the trajectory asymptotically or exponentially. The synthesis of the region involves the verification of an _incremental Lyapunov function_ using a branch-and-cut approach as shown below.
~~~
<video height="320" controls>
  <source src="/assets/research/iroa_proc.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
~~~
Once a suitable incremental region of attraction is found, the attractive region around any trajectory can be efficiently computed. For example, the figure below shows the attractive region around a swing-up trajectory of a torque-limited inverted pendulum. The blue lines indicate simulations started randomly within the attractive region.
![Projection of the incremental region of attraction along a trajectory](/assets/research/iroa_traj.png)
Some of the randomized simulations plotted above are animated in the following GIF.
![A collection of pendulum swing-ups](/assets/research/iroa_pendulum.gif)
This is currently _unpublished_ work, please watch this space for more information.

## Contraction Theory-Based $\mathcal{L}_1$-Adaptive Control
Contraction theory is a tool to analyze _incremental stability_ properties for nonlinear systems and constructively design tracking controllers that stabilize the system around any trajectory. In \citep{zhao21}, we provide synthesis procedures to compute robust control contraction metrics that minimize the $\mathcal{L}_\infty$-gain from the disturbances to the tracking error. Even better performance can be acheived by augmenting the contraction theory-based setup with the $\mathcal{L}_1$-adaptive control architeture to compensate for the disturbances within the control channel \citep{lakshmanan20}. We provide certificates in the form of _tubes_ whose width is adjustable based on the adaptive controller parameters. Furthermore, they can be incorporated into motion planners to provide paths that are safe with respect to the disturbances, as shown below. The figure illustrates the path of 10 unicycle systems with randomized initializations that remain within the tube and avoid collisions with the gray obstacles.
![Tubes for safe feedback motion planning](/assets/research/dubins_cl1gp.png)
While the tubes are tunable based on tracking requirements, their adjustment relies on a trade-off with the inherent robustness of the system to model inaccuracies. In \citep{lakshmanan21}, we show that the performance of the contraction theory-based $\mathcal{L}_1$-adaptive control architecture can be improved by learning any unmodeled dynamics in the system without sacrificing robustness. The GIF below illustrates the improvement in the peformance a vehicle traversing a race track in the form of tighter tubes.
![Performance improvement by learning uncertainties](/assets/research/race_cl1gp.gif)
In the video below, we show the performance of an $\mathcal{L}_1$-adaptive control augmentation to the tracking control of a quadrotor by injecting disturbances in several scenarios \citep{wu21}.
~~~
<iframe height="360"
src="https://www.youtube.com/embed/25Z7iAkZ5xw">
</iframe>
~~~
* \biblabel{lakshmanan20}{Lakshmanan et al. (2020)} A. Lakshmanan[^1], A. Gahlawat[^1], N. Hovakimyan. "[Safe Feedback Motion Planning: A Contraction Theory and $\mathcal{L}_1$-Adaptive Control Based Approach](https://arxiv.org/pdf/2004.01142.pdf)." _Proceedings of the 59th IEEE Conference on Decision and Control (CDC)_, pp. 1578-1583, 2020.
* \biblabel{lakshmanan21}{Lakshmanan et al. (2021)} A. Lakshmanan[^1], A. Gahlawat[^1], L. Song, A. Patterson, Z. Wu, N. Hovakimyan, E. Theodorou. "[Contraction $\mathcal{L}_1$-Adaptive Control using Gaussian Processes](http://proceedings.mlr.press/v144/gahlawat21a/gahlawat21a.pdf)." _Proceedings of the 3rd Conference on Learning for Dynamics and Control_, pp. 1027-1040, 2021.
* \biblabel{zhao21}{Zhao et al. (2021)} P. Zhao, A. Lakshmanan, K. Ackerman, A. Gahlawat, M. Pavone, & N. Hovakimyan. "[Tube-certified trajectory tracking for nonlinear systems with robust control contraction metrics](https://arxiv.org/pdf/2109.04453.pdf)." _Under review at ICRA 2022_.
* \biblabel{wu21}{Wu et al. (2021)} Z. Wu, S. Cheng, K. Ackerman, A. Gahlawat, A. Lakshmanan, P. Zhao, & N. Hovakimyan."[$\mathcal{L}_1$ Adaptive Augmentation for Geometric Tracking Control of Quadrotors](https://arxiv.org/pdf/2109.06998.pdf)." _Under review at ICRA 2022_.
[^1]: Equal contribution

## Fast Collision Detection for Trajectories
Collision checking is a computational bottleneck in motion planning problems. While there exist several fast methods for exact collision checking between convex objects, collision checking for trajectories are generally more ad-hoc — they are typically checked pointwise up to some resolution. In \citep{lakshmanan19}, we provide fast methods to check for collisions for absolutely continuous curves. In the video below, we describe the prodcedure at a high-level, and show an example of how such methods may be employed in sampling-based planning.
~~~
<iframe height="360"
src="https://www.youtube.com/embed/fQUFv93Z-is">
</iframe>
~~~
The collision detection is extensible to situations when only a probabilistic model of the motion of an obstacle is available as a high-probability result \citep{patterson19}. The following figure shows two paths (green and blue), one of which has a higher probability collision than another with an obstacle. The motion of the obstacle is predicted using a gaussian process model based on past data and probabilistic intention.
![Collision avoidance of based on obstacle prediction](/assets/research/intent_collision.gif)
* \biblabel{lakshmanan19}{Lakshmanan et al. (2019)} A. Lakshmanan, A. Patterson, V. Cichella, N. Hovakimyan. "[Proximity Queries for Absolutely Continuous Parametric Curves](https://arxiv.org/pdf/1902.05027.pdf)." _Proceedings of Robotics: Science and Systems XV_, 2019.
* \biblabel{patterson19}{Patterson et al. (2020)} A. Patterson, A. Lakshmanan, N. Hovakimyan. "[Intent-Aware Probabilistic Trajectory Estimation for Collision Prediction with Uncertainty Quantification](https://arxiv.org/pdf/1904.02765.pdf)." _Proceedings of the 58th IEEE Conference on Decision and Control (CDC)_, pp. 3827-3832, 2019.
