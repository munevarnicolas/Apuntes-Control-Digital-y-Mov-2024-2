# Controladores por retroalimentación de Estados 
La clase estuvo dirigida al estudio y analisis sobre la retroalimentación de estados, el cual es un método de control en el que se utiliza información sobre el estado actual de un sistema para ajustar su comportamiento y lograr un rendimiento deseado, por eso las caracterisiticas de controlabilidad y observabilidad en los sistemas MIMO son de gran importancia para que se logre un control robusto y efectivo, ademas se analizo y detallo la metodologia que se usa para su diseño.
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

💡**Ejemplo 1:** 

$$
\begin{bmatrix}
\chi_1(k+1) \\
\chi_2(k+1)
\end{bmatrix}=
\begin{bmatrix}
1.5 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
\chi_{1}(k) \\
\chi_{2}(k)
\end{bmatrix}
+
\begin{bmatrix}
1 \\
0
\end{bmatrix}
u(k)
$$

Se verifica si el sistema es controlable:

$$
U = [BAB]
$$

$$
AB = 
\begin{bmatrix}
1.5 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
1 \\
0
\end{bmatrix}=
\begin{bmatrix}
1.5 \\
1
\end{bmatrix}
$$

$$
U = 
\begin{bmatrix}
1 & 1.5 \\
0 & 1
\end{bmatrix}
$$

Luego, se calcula el determinante para saber si es controlable:

$$
U = \left| 
\begin{matrix} 
1 & 1.5 \\ 
0 & 1 
\end{matrix} 
\right| = 1
$$

El sistema si es controlable.

## 2. Observabilidad

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

💡**Ejemplo 2:** 

$$
\begin{bmatrix}
\chi_1(k+1) \\
\chi_2(k+1)
\end{bmatrix}=
\begin{bmatrix}
1.5 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
\chi_{1}(k) \\
\chi_{2}(k)
\end{bmatrix}
+
\begin{bmatrix}
1 \\
0
\end{bmatrix}
u(k)
$$

Se verifica si el sistema es observable:

$$
v = 
\begin{bmatrix}
C \\
CA
\end{bmatrix}
$$

$$
CA = 
\begin{bmatrix}
2 & -1
\end{bmatrix}
\begin{bmatrix}
1.5 & 1 \\
1 & 0
\end{bmatrix}=
\begin{bmatrix}
2 & 2
\end{bmatrix}
$$

$$
v = 
\begin{bmatrix}
2 & -1 \\
2 & 2
\end{bmatrix}
$$

Se calcula el determinante para saber si es observable:

$$
U = \det 
\begin{bmatrix}
2 & -1 \\
2 & 2
\end{bmatrix}
= 6
$$

El Sistema si es observable


La importancia  de la controlabilidad y observabilidad es de gran relevancia para asegurar que un sistema pueda ser controlado y monitoreado adecuadamente, debido a que determinan la existencia de las soluciones para un problema determinado de control, la falta de estas propiedades puede resultar en sistemas ineficaces o incapaces de alcanzar sus objetivos operativos.

## 3. Control por retroalimentación de estados
El objetivo de asignar los polos del sistema en lazo cerrado mediante ganancias proporcionales es una técnica crucial en el diseño de controladores, que permite modificar el comportamiento dinámico del sistema de manera controlada, esta técnica se basa en la idea de que la ubicación de los polos en el plano complejo influye directamente en las características de respuesta del sistema, como el tiempo de subida, el tiempo de establecimiento y la estabilidad general.
### Metodología de diseño
1) Comprobar controlabilidad:
Es verificar si el sistema es controlable, un sistema se considera controlable si es posible llevarlo desde cualquier estado inicial a cualquier estado final en un tiempo finito mediante la aplicación adecuada de entradas de control.
2) Determinar los Coeficientes del Polinomio Característico (Lazo Abierto):
El siguiente paso consiste en determinar el polinomio característico del sistema en lazo abierto, que se expresa como $$zI - A = z^n + a_1 z^{n-1} + \ldots + a_{n-1} z + a_n$$
Este polinomio describe las dinámicas del sistema y sus raíces (los polos) son fundamentales para entender su comportamiento. Los coeficientes $a_i$.
son esenciales para el análisis posterior y deben ser calculados correctamente para asegurar que el controlador diseñado cumpla con los requisitos deseados.
3) Determinar T, T = UW:
En este paso, se determina la matriz \( T \), donde \( U \) es la matriz de entrada y \( W \) es la matriz de salida. Si el sistema está en forma canónica controlable, entonces \( T = I \), lo que simplifica considerablemente los cálculos posteriores. La forma canónica permite trabajar con un modelo más simple y directo, facilitando la asignación de polos.
4) Determinar el Polinomio Deseado a partir de la ubicación de polos deseada $$z^n + \alpha z^{n-1} + \ldots + \alpha_{n-1} z + \alpha_n$$
Este polinomio refleja las características dinámicas que se desean para el sistema en lazo cerrado, como estabilidad, rapidez de respuesta y sobreimpulso. La selección adecuada de las ubicaciones de los polos es crítica para lograr un rendimiento óptimo del sistema.
5) Calcular la Matriz de Ganancias de Retroalimentación de Estado

$$
K = \begin{bmatrix} \alpha_n - a_n & \alpha_{n-1} - a_{n-1} & \ldots & \alpha_2 - a_2 & \alpha_1 - a_1 \end{bmatrix} T^{-1}
$$

Esta matriz K permite implementar la retroalimentación del estado en el controlador, ajustando así los polos del sistema a las ubicaciones deseadas en el plano   complejo. La retroalimentación asegura que las acciones correctivas sean aplicadas en función del estado actual del sistema, mejorando su respuesta general.


## 4. Conclusiones
* El método de retroalimentación de estados proporciona una forma efectiva de ubicar los polos del sistema en posiciones deseadas dentro del espacio complejo, esta capacidad de asignar polos permite ajustar características dinámicas como la estabilidad, el tiempo de respuesta y el sobreimpulso del sistema. Al modificar estos parámetros, se puede optimizar el rendimiento del sistema según las necesidades específicas de la aplicación.
* Trabajar con sistemas en forma canónica controlable simplifica significativamente el proceso de diseño del controlador. En esta forma, se reduce la complejidad computacional y se minimizan los cálculos necesarios para determinar las ganancias de retroalimentación.
* La controlabilidad y la observabilidad son esenciales en la industria para garantizar que los sistemas de control puedan ser diseñados de manera efectiva, estos conceptos determinan si un sistema puede ser controlado adecuadamente y si se puede obtener información suficiente sobre su estado interno a partir de las salidas, sin estos, un sistema podría no cumplir con los requisitos de rendimiento, lo que podría resultar en fallos operativos o ineficiencias.
* La observabilidad permite tomar decisiones informadas basadas en el estado real del sistema, es importante en entornos donde las condiciones pueden cambiar rápidamente, como en el control de procesos en industrias químicos o en sistemas de transporte, debido a la capacidad de inferir el estado interno a partir de las salidas observadas mejora la capacidad de respuesta ante situaciones imprevistas.

## 5. Referencias
[1] "Apuntes Clase - Jueves 31 Octubre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

