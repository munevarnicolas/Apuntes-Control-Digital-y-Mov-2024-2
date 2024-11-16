# Observadores de estados y error de estado estacionario
La clase estuvo dirigida XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

## 1. Problemas de Control
Tanto en control digital como analogico se tienen problemas de control debido a diversos factores, pero uno que resalta es el error de estado estacionario, por eso se utilizan tecnicas para mitigar o eliminar este error.

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

## 2. Observador de Estados
Los observadores de estado son subsistemas de control que estiman las variables de estado de un sistema a partir de las mediciones de las variables de salida y control, se utilizan cuando no es posible medir los estados de las variables de un sistema por diversas razones. Estas estimaciones se ajustan continuamente mediante la retroalimentación del error entre la salida medida y la salida estimada. Este ajuste dinámico asegura que las estimaciones converjan rápidamente a los valores reales, lo que proporciona precisión y estabilidad al sistema controlado.


$$
x(k+1) - \overline{x}(k+1) = A x(k) + B u(k) - (A \overline{x}(k) + B u(k))
$$

$$
e(k+1) = A x(k) + B u(k) - A \overline{x}(k) - B u(k)
$$

$$
e(k + 1) = A (x(k) - \overline{x}(k))
$$

El error de estimación depende directamente de la matriz A porque:
* Define cómo evoluciona el estado real del sistema.
* Influye en la estabilidad y convergencia del observador.
* Permite ajustar la dinámica del sistema a través de las ganancias del observador.

Por lo tanto, una correcta selección y diseño de A y Kp son fundamentales para minimizar el error de estimación y lograr un rendimiento óptimo del sistema controlado.

$$
x(k+1) - \overline{x}(k+1) = A x(k) + B u(k) - \left((A - K_e C) \overline{x}(k) + B u(k) + K_e y(k)\right)
$$

$$
e(k+1) = (A - K_{e} C) x(k) - (A - K_{e} C) \overline{x}(k)
$$

$$
e(k+1) = (A - K_{e} C) (x(k) - \overline{x}(k))
$$

La ecuación 

$$ e(k + 1) = (A - K_e C) e(k) $$ 

describe cómo evoluciona el error de estimación en un sistema controlado. Aquí, $$ e(k) $$ representa el error en el instante $$ k $$, $$ A $$ es la matriz que describe la dinámica del sistema, $$ K_e $$ es la ganancia del observador, y $$ C $$ es la matriz que relaciona los estados con las salidas.

💡**Ejemplo 1:**

#### 1. Sistema:

$$
A = \begin{bmatrix}
1.799 & -0.8025 \\
1 & 0
\end{bmatrix}
$$

$$
B = \begin{bmatrix}
0.01563 \\
0
\end{bmatrix}
$$

$$
C = \begin{bmatrix}
0 & 11910 & 0 & 1107
\end{bmatrix}
$$

#### 2. Ubicación de Polos del observador:
$$
z = -0.2 \quad \text{y} \quad z = -0.2
$$


#### 3. Comprobación de Observabilidad:
La matriz de observabilidad 

$$O = \begin{bmatrix} C \\
CA \end{bmatrix} = \begin{bmatrix} 0.01191 & 0.01107 \\
0.03245 & -0.00955 \end{bmatrix}$$

$$\text{det}(O) = -0.00047,$$

Por lo que el sistema es observable.

#### 4. Polinomio Característico:
$$P(z) = z^2 - 1.799z + 0.8$$

#### 5. Polinomio Deseado:
$$(z + 0.2)^2 = z^2 + 0.4z + 0.04,$$ con $$\alpha_1 = 0.4,$$  $$\alpha_2 = 0.04$$

#### 6. Cálculo de Ganancias del Observador:

$$
\alpha_{1} = 0.4 \quad \text{y} \quad \alpha_{2} = 0.04
$$

$$
a_{1} = -1.799 \quad \text{y} \quad a_{2} = 0.8
$$

$$
K_e = \begin{bmatrix}
0.0111 & -0.0295 \\
0.0119 & 0.0111
\end{bmatrix}^{-1} 
\begin{bmatrix}
\alpha_{2} - a_{2} \\
\alpha_{1} - a_{1}
\end{bmatrix}
$$


## 3. Conclusiones
* Los observadores de estado permiten estimar variables internas de un sistema que no son medibles directamente, lo que es crucial en aplicaciones industriales donde el monitoreo completo del sistema es costoso o poco viable de ejecutar.
* Los controladores PID tienen redes de atraso y adelanto lo que proporciona mayor flexibilidad en el diseño, esta combinación puede compensar tanto retrasos como avances en el sistema, lo que mejora su rendimiento y capacidad de respuesta en todo el sistema. Además, el proceso de diseño y ajuste de estas redes permite una comprensión de la dinámica del sistema, que contribuye al analisis y la optimización continua de sistemas de control.

## 4. Referencias
[1] "Apuntes Clase - Jueves 7 Noviembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

