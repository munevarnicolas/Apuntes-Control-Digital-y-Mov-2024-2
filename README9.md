# Espacio de Estados
La clase estuvo dirigida a las redes de atraso por analisis en frecuencia, en donde su función principal es modificar la respuesta estacionaria del sistema, minimizando el error sin alterar significativamente la respuesta transitoria. Se utilizan herramientas como los diagramas de Bode porque permiten visualizar la magnitud y la fase de la respuesta del sistema.
## 1. Controladores por análisis en frecuencia
El método algebraico por igualación de modelo es una técnica utilizada en la resolución de sistemas de ecuaciones lineales, particularmente en el contexto de la teoría de control y la modelación matemática. Este método permite encontrar los valores de las incógnitas en un sistema de ecuaciones al igualar expresiones derivadas de las mismas incógnitas. En control si se tiene la función de lazo abierto G(z), y sabemos cuál es la respuesta que quiere lograr, expresada a través de la función de transferencia de lazo cerrado Go(z), se puede calcular la función de transferencia del controlador, C(z) que permitirá alcanzar ese comportamiento deseado. Sin embargo este metodo debe tener en cuenta las siguientes carateristicas:

* La compensación de adelanto de fase mejora razonablemente la respuesta transitoria del sistema, aunque provoca un cambio pequeño en la precisión en estado estable y puede acentuar los efectos del ruido de alta frecuencia. Esto se debe a que el cero del compensador genera un adelanto de fase a bajas frecuencias en relación con el polo, lo que resulta en que el compensador adelanta fase en un rango específico de frecuencias.
* La compensacion de atraso de fase se caracteriza por generar un retraso de fase a frecuencias más bajas en comparación con el punto cero, lo que resulta en un compensador que retrasa la fase dentro de un rango específico de frecuencias. Este tipo de compensador se utiliza principalmente para aumentar el margen de fase en sistemas de control. Su diseño se basa en la adición de un polo y un cero en la función de transferencia, donde el cero se coloca a una frecuencia más baja que el polo, permitiendo así mejorar la estabilidad del sistema al optimizar su respuesta en frecuencia.
* El compensador de adelanto-retraso de fase permite mejorar los márgenes de estabilidad, aumentar el ancho de banda y reducir el error en estado estacionario, minimizando así los problemas relacionados con el ruido. Este compensador se forma a partir del producto de las funciones de transferencia de un compensador de adelanto y uno de retraso, donde el compensador de retraso se sitúa a frecuencias más bajas que el de adelanto.

### 1.1 Control PID 

Un controlador PID (Proporcional, Integral y Derivativo) es un mecanismo de control ampliamente utilizado en sistemas de automatización y control industrial. Su función principal es regular variables como temperatura, presión, velocidad y flujo, mediante un lazo de retroalimentación que ajusta continuamente las salidas en función de la diferencia entre un valor deseado (set-point) y el valor medido del proceso. Tiene tres aspectos fundamentales loscuales son:

*Proporcional (P): Este componente genera una salida proporcional al error actual. Cuanto mayor sea el error, mayor será la acción correctiva aplicada. Esto permite una respuesta rápida a las variaciones.
*Integral (I): Este término acumula el error a lo largo del tiempo, corrigiendo cualquier desviación persistente del set-point. Ayuda a eliminar el error en estado estacionario, pero puede causar oscilaciones si no se sintoniza adecuadamente.
*Derivativo (D): Este componente anticipa futuros errores basándose en la tasa de cambio del error actual. Proporciona una acción correctiva que ayuda a suavizar la respuesta del sistema y reduce el sobreimpulso.

El control PID puede considerarse un caso especial de una red de atraso-adelanto, ya que combina las características de ambos tipos de compensación. En un controlador PID, se integran tres acciones proporcional, integral y derivativa, lo que permite mejorar tanto la respuesta transitoria como la precisión en estado estacionario. La parte proporcional actúa como un compensador de adelanto, aumentando la rapidez de respuesta, mientras que la parte integral ayuda a eliminar el error en estado estacionario, similar al efecto de un compensador de atraso. Al combinar estas funciones, el controlador PID optimiza el rendimiento del sistema, mejorando los márgenes de estabilidad y el ancho de banda.

### 1.2  Márgenes de fase y ganancia

#### Margen de Ganancia
El margen de ganancia es la cantidad que se puede aumentar la ganancia del sistema antes de que se produzca inestabilidad. Se expresa como un factor o en decibelios (dB). Un margen de ganancia positivo indica que el sistema puede soportar incrementos en la ganancia sin volverse inestable. 
El margen de ganancia se define como la diferencia entre la ganancia del sistema en el punto donde la fase alcanza -180 grados y 0 dB. En términos matemáticos, si G(jω) es la función de transferencia del sistema, el margen de ganancia Gm se puede calcular como:

$$
G_m = \frac{1}{|G(j\omega_c)|}
$$

Donde ωc es la frecuencia de cruce de fase, es decir, la frecuencia en la que la fase del sistema es 180 grados. Si ∣G(jωc)∣ es mayor que 1 (0 dB), el margen de ganancia será positivo, lo que indica estabilidad. Si es igual a 1, el sistema estará marginalmente estable, y si es menor que 1, el sistema será inestable.

El margen de ganancia tiene tres interpretacion de acuerfdo al valor que se obtenga:

* Margen Positivo: Indica que hay un rango seguro para aumentar la ganancia sin comprometer la estabilidad del sistema. MG > o
* Margen Cero: Significa que cualquier aumento adicional en la ganancia llevará al sistema a un estado inestable. MG = 0
* Margen Negativo: Indica que el sistema ya está inestable y no puede tolerar ningún aumento en la ganancia. MG < 0

#### Margen de Fase

El margen de fase mide cuánta variación de fase es necesaria para generar una pérdida de estabilidad en la frecuencia de cruce de ganancias. Se mide en la frecuencia donde la ganancia es igual a 0 dB. El margen de fase es una medición de la distancia desde la fase medida hasta el desplazamiento de fase de -180°. En otras palabras, cuantos grados debe disminuir la fase para alcanzar -180°.

El margen de FASE tiene tres interpretacion de acuerfdo al valor que se obtenga:

* Margen Positivo: Indica que hay un rango seguro para aumentar la ganancia sin comprometer la estabilidad del sistema. MP > −180°
* Margen Negativo: Indica que el sistema ya está inestable y no puede tolerar ningún aumento en la ganancia. MP < −180°

En un diagrama de Bode, el margen de fase se representa como la distancia entre la curva que muestra la fase del sistema y la línea horizontal correspondiente a -180 °, evaluada en la frecuencia donde la ganancia es 0 dB. Cuanto más lejos esté esta curva del -180 °, mayor será el margen de fase y mejor será la estabilidad del sistema.

💡**Figura 1:** <br/>

![Figura de prueba](images/diagrambodegananciayfase.png)

Figura 1. Medidas de Margenes de Ganancia y Fase en Diagrama de Bode. 

En loa diagramas de bode se puede analizar los margenes de ganancia y de fase. Si los márgenes de ganancia (MG) y de fase (MP) son positivos, el sistema es estable en lazo cerrado; por lo tanto, es deseable que estos márgenes sean lo más grandes posible. Sin embargo, si MG y MP son cero o negativos, el sistema puede volverse inestable en lazo cerrado.

## 2. Redes de Atraso


$$
C_w = \frac{1 + a T_1 w}{1 + T_1 w}; \quad 0 < a < 1
$$



El diseño de una red de atraso para un sistema análogo implica varios pasos que permiten transformar la planta analógica en un sistema discreto, asegurando que se mantenga la estabilidad y el rendimiento deseado. A continuación se detalla el procedimiento:
* Discretización de la Planta Analógica: Comienza por discretizar la función de transferencia de la planta analógica, obteniendo así su equivalente en el dominio Z, denotado como  G(z). Esto se puede lograr utilizando métodos como la transformación bilineal o el método de retención.
* Transformación a Frecuencia: Una vez que se tiene G(z), se transforma a G(w), donde w es la frecuencia en el dominio continuo. Esta transformación permite analizar cómo se comporta el sistema en términos de frecuencia y es crucial para el diseño del compensador.
* Graficar Diagramas de Bode: A partir de G(w), se generan los diagramas de Bode que representan la magnitud y la fase del sistema en función de la frecuencia. Estos gráficos son esenciales para evaluar las características del sistema, como los márgenes de ganancia y fase para evaluar su comportamiento.
Aplicar el Método de Diseño para C(w): Con los diagramas de Bode, se aplica un método de diseño para determinar el compensador C(w). Este paso implica ajustar los parámetros del controlador para lograr los márgenes deseados y mejorar la estabilidad del sistema.
* Recuperar C(z): Se transforma C(w) a su equivalente en el dominio Z, denotado como C(z). Esto es necesario para poder implementar el controlador en un sistema digital. La relación entre las frecuencias se puede expresar como:

$$
w = \frac{T}{2} \cdot \frac{z + 1}{z - 1}
$$

* Calcular KP: Esto se hace con el fin de garantizar el Requerimiento de error, se determina el valor de la ganancia proporcional que satisfaga los requisitos del sistema, específicamente en términos de error en estado estacionario. Esto implica evaluar la constante de error estacionario y asegurarse de que el sistema pueda alcanzar el nivel deseado de precisión.
* Medicion de Márgenes: Se tiene en cuenta el Kp, luego quese ha establecido, se debe medir los márgenes de ganancia y fase del sistema. Estos márgenes son indicadores clave de la estabilidad del sistema en lazo cerrado. Se utilizan herramientas como diagramas de Bode para visualizar cómo estos márgenes se ven afectados por el ajuste de Kp.
* Calcular Frecuencia: Para poder cumplir con Mp +6°, de debe identificar una nueva frecuencia de cruce donde el margen de fase deseado sea al menos Mp +6°, esta frecuencia se convierte en el nuevo punto donde la ganancia es igual a 0 dB, lo que permite evaluar cómo se comporta el sistema en esta nueva configuración.
* Medir la Atenuación: En este paso, se calcula la atenuación necesaria en la frecuencia seleccionada para cumplir con el margen de fase requerido. La atenuación se puede calcular utilizando la fórmula:

$$
\alpha = -20 \log a
$$


$$
a = 10^{-\frac{\alpha}{20}}
$$


* Calcular T1: Finalmente, se determina el tiempo constante T1 necesario para lograr la atenuación deseada a la frecuencia seleccionada, esto se relaciona con la frecuencia angular ω y se expresa como:


$$
\frac{1}{T_1 a} = \frac{\omega_G}{10}
$$

Donde 𝜔𝐺 es la frecuencia de cruce de la ganancia, y la ganancia que es necesario atenuar en el diagrama (1 década antes de la nueva frecuencia).


## 3. Conclusiones
* En los sistemas de control, las redes de atraso son esenciales porque mejoran la precisión en estado estable, lo que permite que el sistema funcione de manera más confiable, estas se utilizan para reducir la ganancia a altas frecuencias, evitar oscilaciones indeseables y mejorar la estabilidad del sistema. Sin embargo, debido a que su uso puede prolongar el tiempo de respuesta transitoria, se utilizan con frecuencia junto con compensadores de adelanto para optimizar ambos aspectos.
* Los controladores PID tienen redes de atraso y adelanto lo que proporciona mayor flexibilidad en el diseño, esta combinación puede compensar tanto retrasos como avances en el sistema, lo que mejora su rendimiento y capacidad de respuesta en todo el sistema. Además, el proceso de diseño y ajuste de estas redes permite una comprensión de la dinámica del sistema, que contribuye al analisis y la optimización continua de sistemas de control.
## 4. Referencias
[1] "Apuntes Clase - Jueves 26 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

