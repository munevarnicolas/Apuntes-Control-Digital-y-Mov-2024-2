# Controladores por retroalimentación de estados  31 octubre
La clase estuvo dirigida XXXXXXXXXXXXXXXXXXXXXX.
## 1. Controlabilidad
La controlabilidad se refiere a la capacidad de un sistema para ser llevado a cualquier estado dentro de su espacio de estados. Esto significa que, dado un estado inicial y un estado final, debe existir una entrada que permita la transición entre estos estados en un tiempo finito. La condición matemática para que un sistema sea controlable se puede verificar a través de la matriz de controlabilidad, que se construye utilizando las matrices del sistema y el vector de entrada. Un sistema es controlable si esta matriz tiene rango completo, es decir, igual al número de variables de estado del sistema.
### 1.1 Matriz de Controlabilidad

$$
X(k + 1) = AX(k) + Bu(k)
$$

$$
y(k) = CX(k) + Du(k)
$$

Matriz de controlabilidad:

$$
U = [ B \, AB \, A^2B \, A^3B \, \ldots \, A^{n-1}B ]
$$

La matriz de controlabilidad tiene dimensiones que coinciden con las de la matriz $$ A $$ del sistema. Un sistema se considera controlable si el determinante de la matriz de controlabilidad es diferente de cero, lo que indica que existe una entrada que permite llevar el sistema a cualquier estado deseado. Además, en un sistema controlable, el rango de la matriz de controlabilidad es igual al número total de variables de estado del sistema. Esto significa que, para lograr un control efectivo sobre el sistema, es esencial que la matriz de controlabilidad tenga rango completo, lo cual garantiza que se pueden alcanzar todos los estados posibles dentro del espacio de estados del sistema.

### 1.2 Observabilidad

Un sistema es observable si, dada cualquier secuencia de vectores de estado y de control, se puede determinar el estado actual en un tiempo finito utilizando únicamente las salidas. Esto significa que la información proporcionada por las salidas es suficiente para reconstruir el estado del sistema sin ambigüedades. Si un sistema no es observable, hay estados internos que no pueden ser inferidos a partir de las salidas, lo que puede llevar a situaciones donde el controlador no tiene conocimiento completo del sistema y, por lo tanto, no puede cumplir con los requisitos de rendimiento deseados.


$$
X(k + 1) = AX(k) + Bu(k)
$$

$$
y(k) = CX(k) + Du(k)
$$

Matriz de observabilidad:

$$
v = \begin{bmatrix}
C \\
CA \\
CA^2 \\
\vdots \\
CA^{n-1}
\end{bmatrix}
$$

La matriz de observabilidad tiene dimensiones que coinciden con las de la matriz $$ A $$ del sistema. Un sistema se considera observable si el determinante de la matriz de observabilidad es diferente de cero, lo que indica que es posible inferir el estado interno del sistema a partir de las salidas observadas. Además, en un sistema observable, el rango de la matriz de observabilidad es igual al número total de variables de estado. Esto significa que, para garantizar una observación efectiva del sistema, es esencial que la matriz de observabilidad tenga rango completo, lo que permite deducir todos los estados internos a partir de las salidas y asegura que el controlador tenga suficiente información para operar adecuadamente.

## 3. Conclusiones
* En los sistemas de control, las redes de atraso son esenciales porque mejoran la precisión en estado estable, lo que permite que el sistema funcione de manera más confiable, estas se utilizan para reducir la ganancia a altas frecuencias, evitar oscilaciones indeseables y mejorar la estabilidad del sistema. Sin embargo, debido a que su uso puede prolongar el tiempo de respuesta transitoria, se utilizan con frecuencia junto con compensadores de adelanto para optimizar ambos aspectos.
* Los controladores PID tienen redes de atraso y adelanto lo que proporciona mayor flexibilidad en el diseño, esta combinación puede compensar tanto retrasos como avances en el sistema, lo que mejora su rendimiento y capacidad de respuesta en todo el sistema. Además, el proceso de diseño y ajuste de estas redes permite una comprensión de la dinámica del sistema, que contribuye al analisis y la optimización continua de sistemas de control.
## 4. Referencias
[1] "Apuntes Clase - Jueves 26 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

