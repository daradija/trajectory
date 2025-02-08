Derivates from roboticArm8.py from gecco project.
The main objective is trajectory in 2D.
The idea is to detect segment violations.
There are two possible trajectories per rotation segment.
In 3 segments, the total number is limited, in this case $$ 2^3 $$ possibilities.

# Thinking mode

Until now, all projections were realized in order:
- Now we must work in thinking mode.
- Now we need a copy mode.
- A way to add the restrictions.
- A trajectory without a graphic interface.

The idea is to use the population to calculate different trajectories, not to calibrate.

## 8/2/25
There is no need to start with imagination.
A non-visible property is created.
And the possibility to make copies is created.
Then some restrictions are attempted, which are of three types:
- Torsion of the extreme angles.
- Collision with another arm.
- Collision with external object (not at the moment).


