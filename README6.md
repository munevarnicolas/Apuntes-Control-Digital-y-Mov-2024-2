# Análisis en frecuencia y diagramas de Bode
La clase estuvo dirigida al análisis en frecuencia, la cual es una técnica esencial en el diseño y análisis de sistemas de control, especialmente en el ámbito de la instrumentación industrial, debido a que permite evaluar cómo un sistema responde a diferentes frecuencias de entrada, lo que es crucial para garantizar un rendimiento óptimo en aplicaciones industriales.
## 1. Analisis en Frecuencia
El análisis de frecuencia es una técnica que evalúa cómo un sistema dinámico responde a diferentes frecuencias de entrada, permitiendo observar cambios en amplitud y fase. Su importancia radica en que ayuda a entender el comportamiento del sistema, optimizar su rendimiento y diseñar controladores efectivos. Es utilizada para evaluar la respuesta de sistemas dinámicos lineales a entradas periódicas, especialmente señales sinusoidales.Además, facilita la identificación de características críticas como la estabilidad y la resonancia en sistemas de control.

### 1.1 Representacion Matematica
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

### 1.2 Sistemas en Fasores
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


## 2. Diagramas de Frecuencia

Cualquier función de transferencia puede dividirse en sus componentes real e imaginaria, lo que permite calcular la magnitud y la fase en el dominio de la frecuencia. Esta separación es crucial para entender cómo un sistema reacciona a distintas frecuencias, ya que proporciona información esencial sobre su comportamiento dinámico. Los resultados obtenidos se pueden graficar en un plano, facilitando así la visualización de la relación entre magnitud y fase.
Los datos pueden representarse en escalas lineales o logarítmicas (en decibelios), lo que mejora su interpretación. También es posible graficar la magnitud frente a la fase utilizando coordenadas polares, lo que ofrece una representación más clara del comportamiento del sistema. Esta visualización relevante para el análisis y diseño de sistemas de control, ya que permite identificar características clave como la estabilidad y el rendimiento bajo diversas condiciones operativas.

💡**Figura 1:** <br/>

![Figura de prueba](images/diagramabode.png)

Figura 1. Diagrama de Bode.

Un diagrama de Bode es una herramienta gráfica que se utiliza para analizar cómo un sistema responde a diferentes frecuencias. Consiste en dos gráficos: uno que muestra la magnitud (o ganancia) en decibelios y otro que representa la fase en grados, ambos en función de la frecuencia. Este tipo de representación permite entender el comportamiento de circuitos eléctricos y sistemas de control, facilitando la identificación de características importantes como la estabilidad y el rendimiento del sistema.

💡**Figura 2:** <br/>

![Figura de prueba](images/diagrampolar.png)

Figura 2. Diagrama Polar.

El diagrama polar es una representación gráfica que muestra cómo un sistema responde a diferentes frecuencias, utilizando coordenadas polares. En este tipo de diagrama, la magnitud de la respuesta se representa radialmente desde el centro, mientras que la fase se indica en dirección angular. Esto permite visualizar de manera clara y compacta la relación entre magnitud y fase a medida que varía la frecuencia.


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

### 2.1. Análisis Frecuencial en Tiempo Discreto
El análisis frecuencial en tiempo discreto se refiere a cómo se estudian las señales que están definidas solo en momentos específicos, es decir, en puntos discretos de tiempo. Este tipo de análisis es fundamental para entender cómo las señales cambian con el tiempo y cómo se comportan frente a diferentes frecuencias. Para llevar a cabo este análisis, se utilizan herramientas matemáticas como la Transformada de Fourier y la Transformada Z, que permiten descomponer una señal en sus componentes de frecuencia. Debido a que no es posible hacer el analisis en frecuencia directamente en timepo completo se utiliza la transformación bilineal, también conocida como transformación de Tustin, la cual es una técnica matemática utilizada en el diseño de filtros digitales y sistemas de control, tiene como principal función convertir funciones de transferencia analógicas (que operan en el dominio continuo) a sus equivalentes discretos (en el dominio digital). Este proceso se realiza mediante un mapeo que relaciona el plano complejo s (utilizado en sistemas continuos) con el plano z (usado en sistemas discretos), permitiendo así que las características del sistema se mantengan durante la transformación.


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
