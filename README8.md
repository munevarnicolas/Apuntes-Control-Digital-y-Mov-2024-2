# Correción Parcial 2do corte 2024-II
La clase estuvo dirigida a la correcion del parcial de segundo corte del semestre 2 del 2024, de la clase control digital.

$$
G(z) = \frac{1.61 \times 10^{-7} z^3 + 6.25 \times 10^{-7} z + 4.15 \times 10^{-7}}{z^3 - 2.87z^2 + 2.75z - 0.88}
$$

**Los polos son:**

- $$P_1 = -100$$
- $$P_2 = -100$$
- $$P_3 = -100$$
- $$P_4 = -2 + 2.73j$$
- $$P_5 = -2 - 2.73j$$

$$
(z + 100)(z + 100)(z + 100)(z + 2 - 2.73j)(z + 2 + 2.73j)
$$

$$
(z^2 + 200z + 10^4)(z + 100)(z^2 + 2z + 2.73j z + 2z + 4 + 5.46j - 2.73j z - 5.46j + 7.45)
$$

$$
(z^3 + 100z^2 + 200z^2 + 2*10^4 z + 10^6 + 10^4z)(z^2 + 4z + 11.45)
$$

$$
(z^3 + 300z^2 + 3*10^4 z + 10^6) (z^2 + 4z + 11.45)
$$


## 3. Conclusiones
* En los sistemas de control, las redes de atraso son esenciales porque mejoran la precisión en estado estable, lo que permite que el sistema funcione de manera más confiable, estas se utilizan para reducir la ganancia a altas frecuencias, evitar oscilaciones indeseables y mejorar la estabilidad del sistema. Sin embargo, debido a que su uso puede prolongar el tiempo de respuesta transitoria, se utilizan con frecuencia junto con compensadores de adelanto para optimizar ambos aspectos.
* Los controladores PID tienen redes de atraso y adelanto lo que proporciona mayor flexibilidad en el diseño, esta combinación puede compensar tanto retrasos como avances en el sistema, lo que mejora su rendimiento y capacidad de respuesta en todo el sistema. Además, el proceso de diseño y ajuste de estas redes permite una comprensión de la dinámica del sistema, que contribuye al analisis y la optimización continua de sistemas de control.
## 4. Referencias
[1] "Apuntes Clase - Jueves 26 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

