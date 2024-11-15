# Correción Parcial 2do corte 2024-II
La clase estuvo dirigida a la correcion del parcial de segundo corte del semestre 2 del 2024, de la clase control digital.

## 2. Procedimientos:

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


$$
(z^5 + 4z^4 + 11.45z^3 + 300 z^4 + 1.2 * 10^3 z^3 + 3.4 * 10^3 z^2 + 3 * 10^4 z^3 + 12 * 10^4 z^2 + 343.5 * 10^3 z + 10^6 z^2 + 4* 10^6 z + 11.45*10^6)        
$$

$$
(z^5 + 304z^4 + 31,21 * 10^3 z^3 + 1,12 * 10^6 z^2 + 4.34 * 10^6 z + 11.45 * 10^6) 
$$

$$
G_0(z) = \frac{1}{z^5 + 304z^4 + 31,21 * 10^3 z^3 + 1,12 * 10^6 z^2 + 4.34 * 10^6 z + 11.45 * 10^6}
$$

$$
C = \frac{A_{0} + A_{1}z + A_{2}z^2}{B_{0} + B_{1}z + B_{2}z^2}
$$

$$
G_0 = \left( \frac{1.61 \times 10^{-7} \cdot 2^2 + 6.75 \times 10^{-7} \cdot z + 1.53 \times 10^{7}}{2^3 - 7.87x^2 + 2.75z - 0.88} \right) \left( \frac{A_{0} + A_{1}z + A_{2}z^2}{B_{0} + B_{1}z + B_{2}z^2} \right)
$$

$$
G_0 = \frac{\left( \frac{1.61 \times 10^{-7} \cdot z^2 + 6.25 \times 10^{-7} \cdot z + 1.53 \times 10^{-7}}{z^3 - 2.87x^2 + 2.75z - 0.88} \right) \left( \frac{A_{0} + A_{1}z + A_{2}z^2}{B_{0} + B_{1}z + B_{2}z^2} \right)}{1 + \left( \frac{1.61 \times 10^{-7} \cdot z^2 + 6.25 \times 10^{-7} \cdot z + 1.53 \times 10^{-7}}{z^3 - 2.87x^2 + 2.75z - 0.88} \cdot \frac{A_{0} + A_{1}z + A_{2}z^2}{B_{0} + B_{1}z + B_{2}z^2} \right)}
$$

$$
(z^3 - 2.87z + 2.75z - 0.88)(B_{0} + B_1 z + B_2 z^2) + \left( 1.61 \times 10^{-7} z^2 + 6.25 \times 10^{-7} z + 1.53 \times 10^{-3} \right) (A_{0} + A_{1}z + A_{2}z^2)
$$

$$
(z^3B_0 + z^4B_1 + B_2z^5 - 2.87z^2B_0 - 2.87Bz^3 - 2.87B_2z^4 + 2.75B_0z +2.75B_1z^2 + 2.75B_2z^3 - 0.88B_0 - 0.88B_1z - 0.88B_2z^2 + 1.61 \times 10^{-7} A_0z^2 + 1.61 \times 10^{-7} A_1z^3 + 1.61 \times 10^{-7} A_2z^4 + 6.25 \times 10^{-7} A_0z + 6.25 \times 10^{-7} A_1z^2 + 6.25 \times 10^{-7} A_2z^3 + 1.53 \times 10^{-7} A_0 + 1.53 \times 10^{-7} A_1z + 1.53 \times 10^{-7} A_2z^2)
$$

- $$1 = B_2 $$

- $$304 = B_1 - 2.87B_2 + 1.61 \times 10^{-7} A_2$$

- $$31.21 \times 10^{3} = -2.87B_1 + 2.75B_2 + 1.61 \times 10^{-7} A_1 + 6.25 \times 10^{-7} A_2 + B_0$$

- $$1.12 \times 10^{6} = -2.87B_0 + 2.75B_1 + 1.61 \times 10^{-7} A_0 + 6.25 \times 10^{-7} A_1 - 0.88B_2 + 1.55 \times 10^{-7} A_2$$

- $$4.34 \times 10^{6} = 2.75B_0 - 0.84B_1 + 6.25 \times 10^{-7}A_0 + 1.53 \times 10^{-7}A_1$$

- $$11.45 \times 10^{6} = -0.88B_0 + 1.53 \times 10^{-7}A_0$$

## 3. Conclusiones
* Sin lugar a duda, se requiere preparar de mejor manera los parciales, priorizando el manejo del tiempo adecuado junto con ejercicios que fortalezcan y permitan apropiar conceptos de la materia, que son pueden llegar a ser sencillos pero requieren de atencion y preparacion.
## 4. Referencias
[1] "Apuntes Clase - Jueves 26 Septiembre 2024" <br/>
[2] "Ingeniería de control Moderno, Ogata" <br/>
[3] "Diseño de control Análogo y Digital, Chen" <br/>
[4] "E.P.1. Control digital y de mov-05909-2463 - Aulas ECCI" <br/>

