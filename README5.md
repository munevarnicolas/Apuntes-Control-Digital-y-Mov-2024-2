# Métodos Algebráicos
La clase estuvo dirigida a comprender los dos principales metodos algebraicos que permiten modelar cualquier respuesta en lazo cerrado.
## 1. Igualación de modelo por metodos algebraicos
El método algebraico por igualación de modelo es una técnica utilizada en la resolución de sistemas de ecuaciones lineales, particularmente en el contexto de la teoría de control y la modelación matemática. Este método permite encontrar los valores de las incógnitas en un sistema de ecuaciones al igualar expresiones derivadas de las mismas incógnitas. En control si se tiene la función de lazo abierto G(z), y sabemos cuál es la respuesta que quiere lograr, expresada a través de la función de transferencia de lazo cerrado Go(z), se puede calcular la función de transferencia del controlador, C(z) que permitirá alcanzar ese comportamiento deseado. Sin embargo este metodo debe tener en cuenta las siguientes carateristicas:

* No deben resultar cancelaciones polo-zero.
* El modelo objetivo debe ser estable.
* Los zeros (fase no mínima) de la planta serán retenidos en lazo cerrado.
* Los compensadores deben ser causales.
*  𝑟 ≤ 𝑟o

💡**Ejemplo 1:** <br/>

$$
C(z) = \frac{G_{0}(z)}{G(z) \cdot (1 - G_{0}(z))}
$$


$$
C(z) = \frac{1.997z^2 + 0.233z - 1.529}{z^2 + 0.125z - 0.757}
$$


$$
C(z) = \frac{\frac{0.009z + 0.008}{z^2 - 1.801z + 0.818}}{\frac{0.004(z + 1)}{(z^2 - 1.819z + 0.8187)} \cdot \left( 1 - \frac{(0.009z + 0.008)}{z^2 - 1.801z + 0.818} \right)}
$$

$$
C(z) = \frac{\frac{0.009z + 0.008}{z^2 - 1.801z + 0.818}}{\frac{0.004(z + 1)}{(z^2 - 1.819z + 0.8187)} \cdot \left(\frac{(z^2 - 1.801z+ 0.818 - 0.009z - 0.008)}{z^2 - 1.801z + 0.818} \right)}
$$

$$
C(z) = \frac{(0.009z + 0.008)(z^2 - 1.819z + 0.8187)}{0.004(z + 1)(z^2 - 1.801z + 0.818 - 0.009z - 0.008)}
$$



## 2. Igualación de coeficientes

El metodo de igualacion de coeficientes, es un metodo algebraico que tabien permite encontrar los valores de las incógnitas en un sistema de ecuaciones al igualar expresiones derivadas de las mismas incógnitas, sin embargo para este metodo enfocado a control, cuando se conoce la función de transferencia en lazo abierto G(z), y también se sabe dónde se quiere que estén los polos según la respuesta deseada, se puede expresar esto en un polinomio característico. Con esta información, se puede determinar la función de transferencia del controlador C(z) que garantice el comportamiento deseado del sistema.
Este metodo debe tener unas consideraciones importantes para su implementación: 

* La igualación se realiza en el polinomio característico por lo tanto no hay control sobre la ubicación de los ceros del sistema.
* Se multiplican A(z) y D(z) por lo tanto en lazo cerrado debe subir el orden del sistema.
* El orden de C(z) debe ser 1 grado menor con respecto a la planta en lazo abierto.
* Se multiplican B(z) y N(z) por lo tanto las funciones de la planta y del controlador deben ser propias.


💡**Ejemplo 2:** <br/>

$$
C(z) = \frac{B_{0} + B_{1} z}{A_{0} + A_{1} z}
$$


$$
G(z) = \frac{0.0043}{z^2 - 1.819z + 0.8187}
$$

$$
Go(z) = \frac{\frac{B_{0} + B_{1} z}{A_{0} + A_{1} z} \cdot \frac{0.0043}{z^2 - 1.819z + 0.8187}}{1 + \frac{B_{0} + B_{1} z}{A_{0} + A_{1} z} \cdot \frac{0.0043}{z^2 - 1.819z + 0.8187}}
$$

$$
Go(z) = \frac{0.0043(B_{0} + B_{1} z)}{(A_{0} + A_{1} z)(z^2 - 1.819z + 0.8187) + 0.0043 B_{0} + 0.0043 B_{1} z}
$$

$$
Go(s) = \frac{0.0043(B_{0} + B_{1} z)}{A_{1} z^3 + z^2 (A_{0} - 1.819 A_{1}) + (0.8187 A_{1} - 1.819 A_{0} + 0.0043 B_{1}) z + 0.8187 A_{0} + 0.0043 B_{0}}
$$

El Sistema es de tercer orden por eso se deben ubicar3 polos:
* z = 0.91 + 𝑗0.23
* z = 0.91 − 𝑗0.23
* z = 0.91

El polinomio deseado sería:

$$
(z - 0.91 + j0.23)(z - 0.91 - j0.23)(z - 0.91) = z^3 - 2.73z^2 + 2.537z - 0.8017
$$

En lazo Cerrado es:

$$
A_{1} z^3 + z^2 (A_{0} - 1.819 A_{1}) + (0.8187 A_{1} - 1.819 A_{0} + 0.0043 B_{1}) z + 0.8187 A_{0} + 0.0043 B_{0}
$$

Al igualar:

$$
z^3 - 2.73 z^2 + 2.537 z - 0.8017 = A_{1} z^3 + z^2 (A_{0} - 1.819 A_{1}) + (0.8187 A_{1} - 1.819 A_{0} + 0.0043 B_{1}) z + 0.8187 A_{0} + 0.0043 B
$$

Los coeficientes obtenidos para el controlador son:

$$
A_{1} = 1 \\
B_{0} = -12.99 \\
A_{0} = -0.911 \\
B_{1} = 14.23
$$

$$
C(z) = \frac{B_{0} + B_{1} z}{A_{0} + A_{1} z} = -12.99 + 14.23 z - 0.911 + z
$$


### 2.1. Ecuaciones diofánticas
Las ecuaciones diofánticas son ecuaciones algebraicas que involucran dos o más incógnitas y cuyos coeficientes son números enteros. Este metodo algebraico es de gran ayuda debido a que simplifica el metodo de igualacion de coeficientes.


<p align="center">
  <img src= images/diofanticas.png />
</p>


💡**Ejemplo 3:** <br/>


$$
G(z) = \frac{0.09016z - 0.1102}{z^2 - 2.01z + 1}
$$


$$
C(z) = \frac{B_{0} + B_{1} \cdot z}{A_{0} + A_{1} \cdot z}
$$

$$
𝐺o(𝑠) = \frac{\frac{B_{0} + B_{1} z}{A_{0} + A_{1} z} \cdot \frac{0.09016 z - 0.1102}{z^2 - 2.01 z + 1}}{1 + \frac{B_{0} + B_{1} z}{A_{0} + A_{1} z} \cdot \frac{0.09016 z - 0.1102}{z^2 - 2.01 z + 1}}
$$

$$
𝐺o(𝑠) = \frac{(0.09016 z - 0.1102)(B_{0} + B_{1} z)}{(z^2 - 2.01 z + 1)(A_{0} + A_{1} z) + (0.09016 z - 0.1102)(B_{0} + B_{1} z)}
$$

$$
D_{0} = (z + 0.3)(z + 0.2 - 0.1j)(z + 0.2 + 0.1j) = z^3 + 0.7z^2 + 0.17z + 0.015
$$

<p align="center">
  <img src= images/Tabladiafo.png />
</p>


## 4. Conclusiones
* 
*
*
## 5. Referencias
[1] "Apuntes Clase - Jueves 12 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>
