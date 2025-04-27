# Estabilidad
Un sistema lineal o invariante en el tiempo es estable si su respuesta en condiciones naturales tiene a cero en un tiempo indefinido y para que este tipo de sistema sea inestable su respuesta debe crecer ilimitadamente en un tiempo indefinido.
## Teorema del valor final
Esta herramienta nos permite saber cual es el valor del sistema que estamos trabajando en estado estacionario. sin embargo, esto solo funciona cuando el sistema es estable.
Para lograr esto se trabaja bajo el dominio de Laplace siguiendo la siguiente identidad:


$$\displaystyle \lim _ {t \to \infty  } f(t)=\displaystyle \lim_{s \to 0} sF(s)$$

##ejemplo
Para demostrar el funcionamiento de este teorema proponemos la siguiente funcion de transferencia:

$$G(s)=\frac{Y(s)}{U(s)}=\frac{6}{7s+3}$$

$$Y(s)=\frac{6 \cdot U(s)}{7s+3}$$

procedemos a utilizar la identidad mostrada anteriormente donde U(s) es reemplazado segun la entrada que se este trabajando ya sea entrada rampa, escalon o de tipo senoidal. En este caso se utilizara la entrada tipo escalon.

$$\displaystyle \lim_{t \to \infty }sY(s)=\displaystyle \lim_{s \to 0} s\cdot \frac{6\cdot \frac{1}{s}}{7s+3}$$
