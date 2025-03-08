## Parámetros identificacion metodo 2 puntos smith:

- $$T = 0.1515$$
- $$To = 0.119$$
- $$K = 14.07$$  
- $$G_s = e^{-0.119s} \*\frac{14.07}{0.1515s + 1}$$

## Funcion de transferencia en tiempo continuo:
$$
G_s = e^{-0.119s} \*\frac{14.07}{0.1515s + 1}
$$

## Funcion de transferencia en tiempo discreto:

- $$G(z) = z^{-2} \* \frac{5.798z + 0.9986}{z - 0.5168}$$

- $$T_{\text{muestreo}} = 0.001$$

## Sintonizacion PID Ziegler y Nichols

  - $$Kc = 0.0036$$
  - $$Ti = 4.1841$$
  - $$Td = 0.0598$$
