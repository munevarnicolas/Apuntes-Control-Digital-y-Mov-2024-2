# Análisis en frecuencia y diagramas de Bode
La clase estuvo dirigida al análisis en frecuencia, la cual es una técnica esencial en el diseño y análisis de sistemas de control, especialmente en el ámbito de la instrumentación industrial, debido a que permite evaluar cómo un sistema responde a diferentes frecuencias de entrada, lo que es crucial para garantizar un rendimiento óptimo en aplicaciones industriales.
## 1. Analisis en Frecuencia
El análisis de frecuencia es una técnica que evalúa cómo un sistema dinámico responde a diferentes frecuencias de entrada, permitiendo observar cambios en amplitud y fase. Su importancia radica en que ayuda a entender el comportamiento del sistema, optimizar su rendimiento y diseñar controladores efectivos. Es utilizada para evaluar la respuesta de sistemas dinámicos lineales a entradas periódicas, especialmente señales sinusoidales.Además, facilita la identificación de características críticas como la estabilidad y la resonancia en sistemas de control.

## 1.1 Representacion Matematica
Este analisis tiene una representacion matematica la cual es:
R(t)=Asin(ωkT+ϕ) 
la cual describe la respuesta de un sistema dinámico a una entrada sinusoidal, y se puede desglosar en sus componentes para entender su significado, en donde

R(t):
Representa la salida del sistema en función del tiempo. Puede ser cualquier variable que se esté analizando, como desplazamiento, velocidad, o corriente.

A:
Es la amplitud de la señal. Indica la magnitud máxima de la respuesta del sistema. Un valor mayor de A significa que el sistema responderá con una mayor intensidad a la entrada.

sin:
La función seno es una función periódica que describe oscilaciones. En este contexto, indica que la salida del sistema variará de manera sinusoidal a lo largo del tiempo.

ωk:
Es la frecuencia angular del sistema, medida en radianes por segundo. Se relaciona con la frecuencia f (en hertz) mediante la relación ωk =2πf. Esta frecuencia determina cuántas oscilaciones ocurren en un segundo.

T:
Este término puede representar el tiempo transcurrido o una variable relacionada con el tiempo que afecta a la respuesta del sistema.

ϕ:
Es el desfase o fase inicial de la señal, medida en radianes. Indica cómo se desplaza la onda sinusoidal en el tiempo respecto a una referencia. Un desfase diferente puede cambiar el momento en que se alcanza el valor máximo o mínimo de R(t).

## 1.2 Sistemas en Fasores
Los sistemas en fasores son representaciones de señales sinusoidales que asumen una frecuencia constante, expresando la señal en términos de amplitud y fase. En este contexto, se utilizan para simplificar el análisis de sistemas dinámicos, permitiendo representar tanto la entrada como la salida del sistema de manera más manejable. Esta representación es especialmente útil en el análisis de sistemas lineales, donde se pueden aplicar técnicas de transformada para estudiar su comportamiento en frecuencia.

💡**Ejemplo 1:** <br/>

$$
H(z) = \frac{1}{(z - 0.1)(z - 5)}
$$

$$
H(e^{j\omega T}) = \frac{1}{(e^{j\omega T} - 0.1)(e^{j\omega T} - 5)}
$$


$$
H(e^{j\omega T}) = \frac{1}{(\cos(\omega T) + j\sin(\omega T) - 0.1)(\cos(\omega T) + j\sin(\omega T) - 5)}
$$


$$
H(e^{j\omega T}) = \frac{1}{\cos^2(\omega T) - \sin^2(\omega T) - 5.1\sin(\omega T) - 5.1\cos(\omega T) + 0.5 + j2\cos(\omega T)\sin(\omega T)}
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
[1] "Apuntes Clase - Jueves 19 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>
