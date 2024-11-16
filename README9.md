# Espacio de Estados y algunas operaciones
La clase estuvo dirigida a comprender el concepto de espacio de estados, una representación matemática de sistemas dinámicos que incluye no solo las entradas y salidas, sino también variables internas que describen completamente el comportamiento del sistema. Se exploraron las diferencias entre la representación interna, que utiliza variables de estado y ecuaciones de estado, y la representación externa, que se basa en funciones de transferencia. Se enfatizó la importancia del espacio de estados en el análisis de propiedades críticas como la controlabilidad y la observabilidad, especialmente en sistemas complejos como los MIMO (Múltiples Entradas, Múltiples Salidas).

## 1. Espacio de Estados 
El espacio de estados, segun Ogata, es una representación matemática de los sistemas dinámicos que no solo considera las entradas y salidas, sino también otras variables que ayudan a representar de manera más precisa la dinámica del sistema. Esta representación, conocida como representación interna, utiliza variables de estado para describir completamente el comportamiento del sistema en un momento dado, estableciendo relaciones a través de ecuaciones de estado y ecuaciones de salida. En contraste, la función de transferencia se conoce como representación externa, ya que se centra en la relación entre las entradas y salidas sin considerar las variables internas. La flexibilidad del espacio de estados para abordar sistemas complejos facilita el análisis de propiedades críticas como la controlabilidad y la observabilidad, convirtiéndolo en una herramienta invaluable en diversas aplicaciones, desde la ingeniería eléctrica hasta la robótica, donde se requiere un control preciso y efectivo.


💡**Figura 1:** <br/>
![Ejemplo sistema MIMO](images/carro.jpg)


La representacion de estados permite representar sistemas MIMO (Multiple Inputs Multiple Output) las cuales son un poco mas complejas que simplemente las SISO (Single Input Single Output), debido a que permiten representar cambios en el modelo a medida que transcurre el tiempo como lo es un carro autonomo en la Figura 1.

### 1.1 Estado:
Es el conjunto de variables que permiten conocercompletamente el comportamiento de un sistema.

### 1.2 Variables de estado: 
Son las variables que determinan el comportamiento de un Sistema y no necesariamente son medibles.

### 1.3 Ecuaciones de Estados: 
Son un conjunto de varias ecuaciones que describen la dinámica de un sistema mediante un modelo matemático. Este modelo se basa en la relación entre las variables de entrada, salida y estado del sistema.

### Representación Matematica:

Para realizar esta representacion matematica se al menos se debe tener dos varibles de estado, de no ser asi se podria realizar por medio de funcion de transferencia o ecuacion diferencial.

* Ecuación de estado:
  
$$ X(k+1) = f(X(k), U(k), k)$$

* Ecuación de salida:
  
$$Y(k) = g(X(k), U(k), k) $$

Tienen como carateristicas que característicasque Las funciones f y g pueden ser no lineales y dependen del tiempo.

## 2. Representacion Matricial:

$$
X(k + 1) = A(k) \cdot X(k) + B(k) \cdot u(k)
$$

$$
y(k) = C(k)X(k) + D(k)u(k)
$$

Simplificando queda:

$$
X(k + 1) = AX(k) + Bu(k)
$$

$$
y(k) = CX(k) + Du(k)
$$

Donde:
- **A**: Matriz de estados, la cual describe la dinámica del sistema y relaciona el estado actual del sistema con su evolución futura.
- **B**: Matriz de entrada, que relaciona las entradas del sistema con los estados, determinando cómo las señales de entrada afectan la evolución del estado.
- **C**: Matriz de salida, la cual conecta los estados del sistema con las salidas, permitiendo la observación del comportamiento del sistema a partir de sus estados internos.
- **D**: Matriz de transmisión directa, que representa la relación directa entre las entradas y las salidas, indicando cómo una entrada afecta inmediatamente a la salida sin pasar por el estado del sistema.


💡**Ejemplo 1:** <br/>
![Ejemplo sistema MIMO](images/ejemplo_1.jpg)

* Ecuación Diferencial

$$
u(t) - F_k - F_B = m \cdot a
$$

$$
u(t) - K y(t) - B \dot{y}(t) = M \ddot{y}(t)
$$


* La ley de Hooke se expresa como:

$$
K y(t) ---> F_k = k \cdot x
$$

<p align="center">Donde x es la elongación del resorte. .</p>

* Fuerza del Amortiguador:

$$
B \dot{y}(t) ---> F_b = B^* \frac{dx}{dt}
$$

Se discretiza la siguiente ecuación:

$$
u(t) - K y(t) - B \dot{y}(t) = M \ddot{y}(t)
$$

$$
\frac{d}{dkT} x(kT) = \frac{x(k + 1) - x(k)}{T}
$$

$$
M Y(k + 2) - 2M Y(k + 1) + M Y(k) + B T Y(k + 1) - B T Y(k) + T^2 K Y(k) = U T^2
$$

$$
M Y(k + 2) + (B T - 2M) Y(k + 1) + (M - B T + T^2 K) Y(k) = U(k) T^2
$$


## 3. Metodologia: 

- Despejar el Máximo Adelanto de la Ecuación en Diferencias: Identificar y despejar el término que tiene el mayor adelanto temporal (es decir, el término que representa la próxima instancia del sistema). Esto es crucial porque permite establecer una relación clara entre los estados actuales y futuros del sistema. En general, se busca expresar la variable dependiente (como la salida o el estado) en función de sus valores anteriores y las entradas.
- Igualar la Salida a la Variable de Estado: Se establece que la salida del sistema es igual a una de las variables de estado. Esto es fundamental para definir cómo las variables de estado influyen en las salidas del sistema.
- Desplazar Sucesivamente para Obtener las Derivadas de las Variables de Estado: Este paso implica tomar derivadas sucesivas (o diferencias) de las variables de estado para obtener sus tasas de cambio. Dependiendo del tipo de sistema (discreto o continuo), se pueden usar derivadas o diferencias finitas.
- Organizar los Términos de las Ecuaciones de Estado dentro de las Matrices A, B, C y D: Finalmente, todos los términos obtenidos se organizan dentro de matrices específicas.

💡**Ejemplo 2:** <br/>

$$y(k+2) + y(k+1) + 0.16y(k) = 2u(k)$$
Despejando la maxima derivada: $$y(k+2) = -y(k+1) - 0.16y(k) + 2u(k)$$
Entonces:
$$y(k) = x_1(k)$$
$$y(k + 1) = x_{1}(k + 1) = x_{2}(k)$$
$$y(k + 2) = x_{2}(k + 1) = -x_{2}(k) - 0.16 x_{1}(k) + 2 u(k)$$

$$ \begin{bmatrix}
\chi_1(k + 1) \\
\chi_2(k + 2)
\end{bmatrix}
=\begin{bmatrix}
0 & 1 \\
-0.16 & -1
\end{bmatrix}
\begin{bmatrix}
\chi_{1}(k) \\
\chi_{2}(k)
\end{bmatrix}
+
\begin{bmatrix}
0 \\
2
\end{bmatrix}
u
$$

$$
y = 
\begin{bmatrix}
1 & 0
\end{bmatrix}
\begin{bmatrix}
x_{1}(k) \\
x_{2}(k)
\end{bmatrix}
+ 
\begin{bmatrix}
0
\end{bmatrix} u
$$

## 3. Operaciones en el Espacio de Estados

### Espacio de estados a partir de Función de transferencia

Existen diversas formas de estado para obtener la forma de espacio desde la funcion de transferencia, algunas son:
- Forma canónica controlable
- Forma canónica observable
- Forma de Jordan
- Otras.

### Forma Canónica Controlable

$$
G(z) = \frac{b_0 z^n + b_1 z^{n-1} + \dots + b_{n-1} z + b_n}{z^n + a_1 z^{n-1} + \dots + a_{n-1} z + a_n}
$$

Sea el sistema de ecuaciones en forma matricial:

$$
\[\begin{bmatrix}
x_1(k+1) \\
x_2(k+1) \\
\vdots \\
x_{n-1}(k+1) \\
x_n(k+1)
\end{bmatrix}
=\begin{bmatrix}
0 & 1 & 0 & \cdots & 0 \\
0 & 0 & 1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & 1 \\
-a_n & -a_{n-1} & -a_{n-2} & \cdots & -a_1
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k) \\
\vdots \\
x_{n-1}(k) \\
x_n(k)
\end{bmatrix}
+
\begin{bmatrix}
0 \\
0 \\
\vdots \\
0 \\
1
\end{bmatrix}
u(k)
\]
$$

La salida del sistema está definida como:

$$
\[
y(k) =
\begin{bmatrix}
b_n & b_{n-1} & \cdots & b_1
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k) \\
\vdots \\
x_{n-1}(k) \\
x_n(k)
\end{bmatrix}
\]
$$

### Forma Canónica Observable

$$
G(z) = \frac{b_0 z^n + b_1 z^{n-1} + \dots + b_{n-1} z + b_n}{z^n + a_1 z^{n-1} + \dots + a_{n-1} z + a_n}
$$

El sistema de ecuaciones se representa como:

$$
\[
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1) \\
\vdots \\
x_{n-1}(k+1) \\
x_n(k+1)
\end{bmatrix}=
\begin{bmatrix}
0 & 0 & \cdots & 0 & -a_n \\
1 & 0 & \cdots & 0 & -a_{n-1}\\
\vdots & \ddots & \ddots & \vdots & \vdots \\
0 & 0 & \cdots & 0  & -a_2\\
0 & 0 & \cdots & 1 & -a_1
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k) \\
\vdots \\
x_{n-1}(k) \\
x_n(k)
\end{bmatrix}
+
\begin{bmatrix}
b_n \\
b_{n-1} \\
\vdots \\
b_2 \\
b_1
\end{bmatrix}
u(k)
\]
$$

$$
y(k) = 
\begin{bmatrix}
0 & 0 & \cdots & 0 & 1
\end{bmatrix}
\begin{bmatrix}
x_{1}(k) \\
x_{2}(k) \\
\vdots \\
x_{n-1}(k) \\
x_{n}(k)
\end{bmatrix}
$$

### Forma Canónica Observable

Si se conocen los polos de la función de transferencia y todos son diferentes:

$$
P_1 = z_1; \quad P_2 = z_2; \quad \ldots ; \quad P_n = z_n
$$

El sistema de ecuaciones se representa como:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1) \\
\vdots \\
x_{n-1}(k+1) \\
x_n(k+1)
\end{bmatrix}
=\begin{bmatrix}
P_1 & 0 & \cdots & 0 & 0 \\
0 & P_2 & \cdots & 0 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & \cdots & P_{i} & 0 \\
0 & 0 & \cdots & 0 & P_n
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k) \\
\vdots \\
x_{n-1}(k) \\
x_n(k)
\end{bmatrix}
+
\begin{bmatrix}
1 \\
1 \\
\vdots \\
1 \\
1
\end{bmatrix} u(k)
$$

$$
y(k) = 
\begin{bmatrix}
c_1 & c_2 & \cdots & c_{n-1} & c_n
\end{bmatrix}
\begin{bmatrix}
x_{1}(k) \\
x_{2}(k) \\
\vdots \\
x_{n-1}(k) \\
x_{n}(k)
\end{bmatrix}
$$

## 4. Raices del Polinomio Caracteristico

Cálculo de los polos en el espacio de estados

$$
|zI - A| = 0
$$

$$
A = 
\begin{bmatrix}
0 & -1 & 0 \\
0 & 0 & 1 \\
-6 & -11 & -6
\end{bmatrix}
$$

$$
|z\cdot 
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}-
\begin{bmatrix}
0 & -1 & 0 \\
0 & 0 & 1 \\
-6 & -11 & -6
\end{bmatrix}|
$$

$$
\left| 
\begin{bmatrix}
z & 0 & 0 \\
0 & z & 0 \\
0 & 0 & z
\end{bmatrix} - 
\begin{bmatrix}
0 & -1 & 0 \\
0 & 0 & 1 \\
-6 & -11 & -6
\end{bmatrix} 
\right|
$$

$$
\det \begin{bmatrix}
z & 1 & 0 \\
0 & z & -1 \\
6 & 11 & z + 6
\end{bmatrix}
$$

Hallando los determinante por cofactores:

$$
=z \left( z(z + 6) - 11(-1) - (-1)(0(z + 6) - 6(-1)) + 0(0 \cdot 11 - 6z) \right)
$$

Polinomio Carateristico:

$$
z^3 + 6z^2 + 11z + 6 = 0
$$

- $z = -1$
- $z = -2$
- $z = -3$

# 5. Espacio de Estados a Función de Transferencia

Consideremos un sistema discreto representado por las siguientes ecuaciones en espacio de estados:

$$\mathbf{x}(k+1) = A \mathbf{x}(k) + B \mathbf{u}(k)$$

$$\mathbf{y}(k) = C \mathbf{x}(k) + D \mathbf{u}(k)$$

Al aplicarse la transformada Z:

$$z \mathbf{X}(z) = A \mathbf{X}(z) + B \mathbf{U}(z)$$
   
$$\mathbf{Y}(z) = C \mathbf{X}(z) + D \mathbf{U}(z)$$

Despejar $$\frac{Y(z)}{U(z)}$$ :

$$
zX(z) - AX(z) = BU(z)
$$

$$
(zI - A)X(z) = BU(z)
$$

$$
X(z) = (zI - A)^{-1} BU(z)
$$

$$
Y(z) = C X(z) + D U(z) \Rightarrow Y(z) = C \left( (zI - A)^{-1} B U(z) \right) + D U(z)
$$

$$
Y(z) = \left( C \left( (zI - A)^{-1} B \right) + D \right) U(z) \longrightarrow \frac{Y(z)}{U(z)} = C \left( (zI - A)^{-1} B \right) + D
$$

   

## 6. Conclusiones
* El espacio de estados facilita el análisis de propiedades críticas como la controlabilidad y la observabilidad, que son de gran importancia para el diseño de controladores efectivos, la comprension de cómo se pueden manipular los estados internos del sistema mediante las entradas, y cómo estos estados pueden ser inferidos a partir de las salidas, es fundamental para garantizar un control robusto y eficiente en aplicaciones industriales.
* A diferencia de la representación mediante funciones de transferencia, que se restringe a sistemas lineales y en estado estacionario, el enfoque del espacio de estados ofrece una flexibilidad considerable al permitir la modelación de sistemas no lineales y dependientes del tiempo, esta capacidad es fundamental, ya que muchos sistemas reales en diversas disciplinas, como la ingeniería eléctrica, la robótica y la automatización, tienen comportamientos con multiples entradas y salidad complejas que no pueden ser capturados adecuadamente por las funciones de transferencia tradicionales.
* La organización de las ecuaciones en matrices A, B, C y D simplifica el análisis matemático, ademas  también proporciona una estructura clara para implementar algoritmos computacionales en simulaciones y control para mayor precision con herramientas como MatLab, para mejorar la efectividad del control en sistemas dinámicos, permitiendo un rendimiento mejor y adaptable en diversas aplicaciones.
* 

## 7. Referencias
[1] "Apuntes Clase - Jueves 26 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

