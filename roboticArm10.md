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

## 9/2/25
Uno de los problemas que aparecen es la comparación que no permite aplicar las mismas operaciones en las diferentes opciones de la guarda.
Para ello lo que se va a hacer es limitar los valores tanto por arriba como por abajo. Y esta operación, que es posible en un numpy La va a llevar a cabo autofore.

`np.where` is a function in the NumPy library that returns elements chosen from `x` or `y` depending on the condition provided. It is often used for element-wise selection based on a condition. The syntax is:

```python
np.where(condition, x, y)
```

- `condition`: An array-like structure that represents the condition to be checked.
- `x`: Values from which to choose when the condition is True.
- `y`: Values from which to choose when the condition is False.
