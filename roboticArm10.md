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
One of the problems that arise is the comparison that does not allow applying the same operations in the different options of the guard.
To address this, the values will be limited both above and below. And this operation, which is possible in NumPy, will be carried out by autofore.

`np.where` is a function in the NumPy library that returns elements chosen from `x` or `y` depending on the condition provided. It is often used for element-wise selection based on a condition. The syntax is:

```python
np.where(condition, x, y)
```

- `condition`: An array-like structure that represents the condition to be checked.
- `x`: Values from which to choose when the condition is True.
- `y`: Values from which to choose when the condition is False.

En el momento en el que llegas a una guarda, en el IF, es donde nace la reproducción genética que es necesaria para la autodiferenciación. 
El valor de comparación de la guarda si tiene pseudo gradientes será sometido a un proceso de selección natural. Más concretamente, yo diría que la  seguía sometido un proceso de selección natural y el valor con el que se compara si tiene pseudo gradiente sería optimizado.
Hasta ahora, una vez que se calculaba el error, se corregían todos los parámetros según los gradientes del error. El problema del pseutoparámetro es que no está definido su origen como parámetros dentro del autofore. Podríamos anotar la delta. Pero dado que a veces queremos realizar un id3 para estimar el desempeño de las distintas soluciones, así como su coherencia con los gradientes. 

Dado un conjunto de puntos x,y con sus pendientes from scipy.interpolate import CubicSpline puede ser usada.
Me pregunto si habrá métodos robustos, con ruido y error para hacer estas aproximaciones.
Dado los puntos se pueden detectar las incoherencias o rugosidades del problema. Si es muy rugoso es que la resolución de puntos no es apropiada. En n dimensiones a lo mejor hay solución. 
Es como meter una dimensión mas, si tienes una constante, es inclinar la recta.
Si tieenes dos puntos es como hacer una curva de tercer grado. Grado dos pasa por dos puntos, si quieres forzar la pendiente tienes que meter un grado mas. 
Es como añadir el punto que está entre los dos extremos, como rectas que se corta, pueden ser curvas si es la hessiana. Esto significa que se puede aplicar regresión múltiple para resolver el polinomio. O lo que es lo mismo, definible mediante un polinomio.

El problema es cuando los elementos no son continuos. Una comparación, una función. 

----

Los siguientes tipos de restricciones, unas que provienen del propio ángulo que puede alcanzar el segmento robótico , otro de tipo puntual, y otro de cruce de segmentos.  Una pared es un segmento fijo, en 2D. Primero 2D y luego 3D.
Y con respecto al algoritmo, si una ruta se choca, pues se prueba otra. Otra posibilidad es gravitatoria, una fuerza de repursión que empuja los segmentos que se acercan.
Podemos simular que se choca y luego poner la fuerza, repitiendo la simulación.
Y por último, lo he puesto en el github, la posibilidad de poner cámaras y detectar los obstáculos a evitar con lo cual combino todos los elementos.