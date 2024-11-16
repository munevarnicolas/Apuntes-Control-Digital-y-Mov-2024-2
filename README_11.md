# Observadores de estados y error de estado estacionario
La clase estuvo dirigida XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

## 1. Problemas de Control
Tanto en control digital como analogico se tienen porblemas de control debido a diversos factores, pero uno que resalta es el error de estado estacionario.

### Regulación 
La regulación se refiere al proceso mediante el cual un sistema de control mantiene una variable en un valor deseado (referencia) que es igual a cero. En este contexto, el objetivo principal es eliminar cualquier desviación de este valor, asegurando que la salida del sistema permanezca constante a pesar de las perturbaciones externas. Este tipo de control es crucial en aplicaciones donde es necesario estabilizar una variable, como la temperatura en un horno o la presión en un tanque.

$$
x(\infty) = 0
$$


### Servosistemas
El servo se refiere a sistemas donde al menos uno de los estados tiene una referencia diferente de cero. En este caso, el sistema no solo busca mantener un valor constante, sino que también responde a cambios en la entrada de referencia r(t). El objetivo es que, a largo plazo, la salida del sistema se iguale a esta referencia.

$$
y(\infty) = y_{ss}
$$

$$
r(\infty) = r_{ss}
$$

$$
e_{ss} = r_{ss} - Y_{ss}
$$

$$
e_{ss} = 0
$$


### Seguimiento Integral

La propuesta de una ley de control que incluye un vector de ganancias F para la referencia es un enfoque común en el diseño de sistemas de control, especialmente en el contexto de control por realimentación de estados. Este método permite mejorar el seguimiento de una referencia deseada y optimizar el comportamiento dinámico del sistema.La ley de control se define como:

$$
x(k + 1) = Ax(k) + Bu(k)
$$

$$
u(k) = -Kx(k) + Fr(k)
$$

Donde:
- u(k) es la acción de control.
- K es la matriz de ganancias que se aplica a los estados del sistema 
- F es el vector de ganancias para la referencia.
- r(k) es la señal de referencia que se desea seguir.

Se reemplaza la acción de control en la ecuación de estados:

$$
x(k + 1) = (A - BK)x(k) + BFr(k)
$$


$$
y(k) = Cx(k)
$$

La creación de una nueva variable de estados para compensar la referencia en un sistema de control se basa en la necesidad de mejorar el seguimiento de la señal de referencia y mitigar el error en estado estacionario. Esto se logra mediante un esquema de control integral, que es de suma importancia en el diseño de sistemas de control.
La introducción de una nueva variable de estados, denotada como \( v(k) \), tiene como objetivo principal compensar el error entre la referencia deseada \( r(k) \) y la salida del sistema \( y(k) \). La ecuación que describe esta nueva variable es:

$$
v(k + 1) = v(k) + r(k) - y(k)
$$

Nuevas ecuaciones de estados:

$$
x(k + 1) = Ax(k) + Bu(k)
$$

$$
v(k + 1) = v(k) + r(k) - y(k)
$$

$$
y(k) = Cx(k)
$$

$$
v(k + 1) = v(k) + r(k) - Cx(k)
$$

$$
\begin{bmatrix}
x(k + 1) \\
v(k + 1)
\end{bmatrix}=
\begin{bmatrix}
A & 0 \\
-C & 1
\end{bmatrix}
\begin{bmatrix}
x(k) \\
v(k)
\end{bmatrix}
+
\begin{bmatrix}
B \\
0
\end{bmatrix}
u(k)
+
\begin{bmatrix}
0 \\
1
\end{bmatrix}
r
$$

$$
y(k) = \begin{bmatrix} C & 0 \end{bmatrix} \begin{bmatrix} \chi(k) \\ \upsilon(k) \end{bmatrix}
$$

$$
u = -K \cdot x + K_{i} \cdot v
$$

$$
u = - \begin{bmatrix} K & -K_{i} \end{bmatrix} \begin{bmatrix} \chi \\ \upsilon \end{bmatrix}
$$

$$
u = - K_{a} \cdot x_{a}
$$

$$
x_a(k + 1) = A_a x_a(k) + B_a u + B_r r
$$

$$
y(k) = C_a x_a
$$

$$
x(k + 1) = A_{a} x_{a} + B_{a} (- K_{a} x_{a}) + B_{r} r
$$

$$
x(k + 1) = A_{a} x_{a} - B_{a} K_{a} x_{a} + B_{r} r
$$

$$
x(k + 1) = (A_{a} - B_{a} K_{a}) x_{a} + B_{r} r
$$

$$
x(k + 1) = A_{aLC} x_{a} + B_{r} r
$$

## 3. Conclusiones
* En los sistemas de control, las redes de atraso son esenciales porque mejoran la precisión en estado estable, lo que permite que el sistema funcione de manera más confiable, estas se utilizan para reducir la ganancia a altas frecuencias, evitar oscilaciones indeseables y mejorar la estabilidad del sistema. Sin embargo, debido a que su uso puede prolongar el tiempo de respuesta transitoria, se utilizan con frecuencia junto con compensadores de adelanto para optimizar ambos aspectos.
* Los controladores PID tienen redes de atraso y adelanto lo que proporciona mayor flexibilidad en el diseño, esta combinación puede compensar tanto retrasos como avances en el sistema, lo que mejora su rendimiento y capacidad de respuesta en todo el sistema. Además, el proceso de diseño y ajuste de estas redes permite una comprensión de la dinámica del sistema, que contribuye al analisis y la optimización continua de sistemas de control.

## 4. Referencias
[1] "Apuntes Clase - Jueves 7 Noviembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

