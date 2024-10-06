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
C(z) = \frac{{0.009z + 0.008)} {2x} }{ \frac{0.004(z + 1)}{z^2 - 1.819z + 0.8187} \cdot \left( 1 - \frac{(0.009z + 0.008)}{z^2 - 1.801z + 0.818} \right) }
$$





## 2. Igualación de coeficientes

El metodo de igualacion de coeficientes, es un metodo algebraico que tabien permite encontrar los valores de las incógnitas en un sistema de ecuaciones al igualar expresiones derivadas de las mismas incógnitas, sin embargo para este metodo enfocado a control, cuando se conoce la función de transferencia en lazo abierto G(z), y también se sabe dónde se quiere que estén los polos según la respuesta deseada, se puede expresar esto en un polinomio característico. Con esta información, se puede determinar la función de transferencia del controlador C(z) que garantice el comportamiento deseado del sistema.
Este metodo debe tener unas consideraciones importantes para su implementación: 

* La igualación se realiza en el polinomio característico por lo tanto no hay control sobre la ubicación de los ceros del sistema.
* Se multiplican A(z) y D(z) por lo tanto en lazo cerrado debe subir el orden del sistema.
* El orden de C(z) debe ser 1 grado menor con respecto a la planta en lazo abierto.
* Se multiplican B(z) y N(z) por lo tanto las funciones de la planta y del controlador deben ser propias.




💡**Ejemplo 2:** <br/>
FALTA HACER EJEMPLO 2
$$
\[ G(z) = \frac{4}{z^3 - 7.8z^2 + 13.4z + 3} \]
$$

<p align="center">
Se busca la ubicacion de los polos:
</p>

$$
\[ z^3 - 7.8z^2 + 13.4z + 3 = 0 \]  
$$

<p align="center">
z = 5
</p>
<p align="center">
z = 3
</p>
<p align="center">
z = -0.2
</p>
<p align="center">
El Sistema es inestable debido a que hay 2 polos por fuera del círculo unitario
</p>

### 2.1. Ecuaciones diofánticas
Las ecuaciones diofánticas son ecuaciones algebraicas que involucran dos o más incógnitas y cuyos coeficientes son números enteros. Este metodo algebraico es de gran ayuda debido a que simplifica el metodo de igualacion de coeficientes.

💡**Ejemplo 3:** <br/>
FALTA HACER EL EJEMPLO 3



## 3. Ejercicios
FALTANNNN

## 4. Conclusiones
*
*
*
## 5. Referencias
[1] "Apuntes Clase - Jueves 12 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>
