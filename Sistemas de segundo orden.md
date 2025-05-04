# Sistemas de segundo orden
Daniel Felipe Ladino, Angel David Melo
Se le conoce como los sistemas que tienen dos polos en su funcion de transferencia.
Estos sistemas tienen la siguiente estructura:

$$\frac{\mathrm{d^{2}} y(t)}{\mathrm{d} t^{2}}+a_{1}\frac{\mathrm{d} y(t)}{\mathrm{d} t}+a_{0}y(t)=b_{0}u(t)$$

Para encontrar la funcion de trasferencia de estos sistemas se siguen los siguientes pasos:
Primero se aplica transformada de Laplace a la ecuacion

$$s^{2}Y(s)+a_{1}sY(s)+a_{0}Y(s)=b_{0}U(s)$$

Despues se despeja la ecuacion para obtener la funcion de transferencia

$$\frac{Y(s)}{U(s)}=\frac{b_{0}}{s^{2}+a_{1}s+a_{0}}$$

## Forma canonica
