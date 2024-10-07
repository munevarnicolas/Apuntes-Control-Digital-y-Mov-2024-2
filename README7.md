# Diseño de redes de atraso por análisis en frecuencia
La clase estuvo dirigida a las redes de atraso por analisis en frecuencia, en donde su función principal es modificar la respuesta estacionaria del sistema, minimizando el error sin alterar significativamente la respuesta transitoria. Se utilizan herramientas como los diagramas de Bode porque permiten visualizar la magnitud y la fase de la respuesta del sistema.
## 1. Controladores por análisis en frecuencia
El método algebraico por igualación de modelo es una técnica utilizada en la resolución de sistemas de ecuaciones lineales, particularmente en el contexto de la teoría de control y la modelación matemática. Este método permite encontrar los valores de las incógnitas en un sistema de ecuaciones al igualar expresiones derivadas de las mismas incógnitas. En control si se tiene la función de lazo abierto G(z), y sabemos cuál es la respuesta que quiere lograr, expresada a través de la función de transferencia de lazo cerrado Go(z), se puede calcular la función de transferencia del controlador, C(z) que permitirá alcanzar ese comportamiento deseado. Sin embargo este metodo debe tener en cuenta las siguientes carateristicas:

* La compensación de adelanto de fase mejora razonablemente la respuesta transitoria del sistema, aunque provoca un cambio pequeño en la precisión en estado estable y puede acentuar los efectos del ruido de alta frecuencia. Esto se debe a que el cero del compensador genera un adelanto de fase a bajas frecuencias en relación con el polo, lo que resulta en que el compensador adelanta fase en un rango específico de frecuencias.
* La compensacion de atraso de fase se caracteriza por generar un retraso de fase a frecuencias más bajas en comparación con el punto cero, lo que resulta en un compensador que retrasa la fase dentro de un rango específico de frecuencias. Este tipo de compensador se utiliza principalmente para aumentar el margen de fase en sistemas de control. Su diseño se basa en la adición de un polo y un cero en la función de transferencia, donde el cero se coloca a una frecuencia más baja que el polo, permitiendo así mejorar la estabilidad del sistema al optimizar su respuesta en frecuencia.
* El compensador de adelanto-retraso de fase permite mejorar los márgenes de estabilidad, aumentar el ancho de banda y reducir el error en estado estacionario, minimizando así los problemas relacionados con el ruido. Este compensador se forma a partir del producto de las funciones de transferencia de un compensador de adelanto y uno de retraso, donde el compensador de retraso se sitúa a frecuencias más bajas que el de adelanto.


💡**Ejemplo 1:** <br/>
FALTA HACER EJEMPLO 1

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
[1] "Apuntes Clase - Jueves 26 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

