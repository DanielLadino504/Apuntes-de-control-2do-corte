# Estabilidad
Un sistema lineal o invariante en el tiempo es estable si su respuesta en condiciones naturales tiene a cero en un tiempo indefinido y para que este tipo de sistema sea inestable su respuesta debe crecer ilimitadamente en un tiempo indefinido.
## Teorema del valor final
Esta herramienta nos permite saber cual es el valor del sistema que estamos trabajando en estado estacionario. sin embargo, esto solo funciona cuando el sistema es estable.
Para lograr esto se trabaja bajo el dominio de Laplace siguiendo la siguiente identidad:


$$\displaystyle \lim _ {t \to \infty  } f(t)=\displaystyle \lim_{s \to 0} sF(s)$$

##ejemplo
Para demostrar el funcionamiento de este teorema proponemos la siguiente funcion de transferencia para evaluar la estabilidad de este sistema con una entrada especifica.

$$G(s)=\frac{Y(s)}{U(s)}=\frac{6}{7s+3}$$

$$Y(s)=\frac{6 \cdot U(s)}{7s+3}$$

procedemos a utilizar la identidad mostrada anteriormente donde U(s) es reemplazado segun la entrada que se este trabajando ya sea entrada rampa, escalon o de tipo senoidal. En este caso se utilizara la entrada tipo escalon.

$$\displaystyle \lim_{t \to \infty }sY(s)=\displaystyle \lim_{s \to 0} s\cdot \frac{6\cdot \frac{1}{s}}{7s+3}$$

## Analisis de estabilidad por ubicacion
Para determinar si un sistema dinamico es estable o no, se puede determinar su estado encontrando los polos dominantes del sistema.Usando esto podemos determinar el comportamiento del sistema por medio de las siguientes condiciones:

1. Si alguno de los polos se encuentran al lado derecho de la grafica el sistema es inestable. 

2. Todos los polos del sistema deben estar en el lado izquiero para que el sistema sea estable.

## Ejemplo
Para demostrar su funcionamiento se hara una breve demostracion con la siguiente funcion de transferencia:

$$G(s)=\frac{7s}{6s+1}\to 6s+1=0\to s=-\frac{1}{6}$$

## Criterio de Routh-Hurwitz
Para poder decir que se tiene un pilonomio de hurwitz sus raices deben tener parte real negativa. Este criterio permite identificar estos polinomios de una manera mas sencilla
