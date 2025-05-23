# Controlador proporcional
Daniel Felipe Ladino, Angel David Melo

Un sistema que contiene un controlador proporcional o tambien conocido como un controladdor PID es un tipo de sistema de realimentacion lineal, en donde el factor de correccion es proporcional a la diferencia.
Una de sus caracteristicas es que el valor objetivo nunca es alcanzado y mientras la diferencia se acerque a cero mas se acercara a cero la correccion aplicada.
## De que trata?
Para empezar se debe tener en claro que variable se quiere controlar para comparar el valor que se tiene hasta el momento con el valor deseado para empezar a realizar el controlador.
# Retroalimentacion
![](13.png)

En lazo cerrado para cambiar el tiempo de respuesta del sistema se debe cambiar la planta de manera que sea un sistema en lazo cerrado añadiendo un controlador y esto no solo puede permitir que el sistema sea mas rapido al momento de enviar la respuesta de interes tambien puede llegar a mejorar el desempeño del sistema.
# control ON-OFF
![](on-off.jpg)

Se trata de un sistema con un controlador que activa o desactiva una salida de forma binaria sin algun estado intermedio, se puede encontrar en sistemas que tienen dos posiciones estables como el encendido o apagad o.
# controlador de accion proporcional
![](sin-tc3adtulo1.png)

En este tipo de controlador se multiplica el error del sistema con una costante diseñada para conseguir el funcionamiento deseado.

# ejemplo 1

Tenemos el siguiente sistema en lazo cerrado:

$$G(s)=\frac{0.25}{s+2}$$

Lo pasamos a su forma canonica:

$$G(s)=\frac{\frac{0.25}{2}}{\frac{s}{2}+1}$$

Con esto podemos sacar los siguientes valores:

$$K=0.125$$

$$\tau=\frac{1}{2}=0.5 segundos$$

y sabiendo la formula para el tiempo de estabilizacion podemos encontrar su valor:

$$t_{s}=4\tau =4(0.5)=2 segundos$$

Nota: en este caso se propuso dividir a la mitad el tiempo de estabilizacion por lo que t_{s}=1

Volivendo al ejercicio obtenemos la funcion de transferencia en lazo cerrado:

$$G_{0}(s)=\frac{K_{p}G(s)}{1+K_{p}G(s)}$$

$$G_{0}(s)=\frac{K_{p}\frac{0.25}{s+2}}{1+K_{p}\frac{0.25}{s+2}}$$

$$G_{0}(s)=\frac{Y}{R}=\frac{0.25K_{p}}{s+2+0.25k_{p}}$$

Finalmente se propone la funcion de transferencia en lazo cerrado y su forma canonica:

$$G_{0}(s)=\frac{\frac{0.25K_{p}}{s+2+0.25K_{p}}}{1+\frac{s}{2+0.25K_{p}}}$$

Teniendo la funcion de transferencia se propone la ecuacion para el valor del controlador:

$$\tau =\frac{1}{2+0.25K_{p}}$$

$$t_{s}'=4\tau =\frac{4}{2+0.25K_{p}}=1$$

$$4=2+0.25K_{p}$$

$$K_{p}=\frac{4-2}{0.25}=8$$

# Ejemplo 2

Para el siguiente sistema se debe diseñar un controlador de accion proporcional que haga que el sistema sea sub amortiguado

$$G(s)=\frac{1}{S^{2}+8s+15}$$

Se plantea la respuesta del sistema en lazo abierto

$$W_{n}=\sqrt{15}$$

$$2\zeta \sqrt{15}=8$$

$$\zeta=\frac{8}{2\sqrt{15}}=1.03$$

El sistema actualmente sobre-amortiguado

Obtenemos la funcion de transferencia en lazo cerrado del sistema:

$$G_{0}(s)=\frac{K_{p}G(s)}{1+K_{p}G(s)}=\frac{K_{p}\frac{1}{s^{2}+8s+15}}{1+K_{p}\frac{1}{s^{2}+8s+15}}$$

$$G_{0}(s)=\frac{K_{p}}{s^{2}+8s+15+K_{p}}$$

Despues de esto empezamos a calcular el valor del controlador ademas de colocarle un valor a \zeta que en este caso sera 0.85

$$2\zeta W_{n}=2\cdot 0.85 \sqrt{15+K_{p}}=8$$

$$2\zeta W_{n}=1.7 \sqrt{15+K_{p}}=8\to \sqrt{15+K_{p}}=\frac{8}{1.7}$$

$$(\sqrt{15+K_{p}})^{2}=(\frac{8}{1.7})^{2}\to 15+K_{p}=22.14$$

$$K_{p}=22.14-15=7.14$$

# Ejercicios
## ejercicio #1
Se tiene la siguiente funcion de tranferencia y se necesita que el sistema sea sobre-amortiguado

$$\frac{3}{s^{2}+3s+3}$$

Planteamos la respuesta del sistema en lazo abierto:

$$w_{n}=\sqrt{3}$$

$$2\zeta \sqrt{3}=3$$

$$\zeta=\frac{3}{2\sqrt{3}}=0.86$$

Como podemos ver el sistema actualmente es sub-amortiguado.
Planteamos la ecuacion para el controlador proporcional:

$$G_{0}(s)=\frac{k_{p}\frac{3}{s^{2}+3s+3}}{1+K_{p}\frac{3}{s^{2}+3s+3}}$$

De esta operacion nos queda:

$$G_{0}(s)=\frac{3k_{p}}{s^{2}+3s+3+k_{p}}$$

Despues de esto empezamos a calcular el valor de k poniendo el valor deseado de zeta, en este caso sera 1.07:

$$2\zeta w_{n}=2\cdot 1.07\cdot \sqrt{3+k_{p}}=3$$

$$(\sqrt{3+k_{p}})^{2}=(\frac{3}{2.14})^{2}$$

$$3+k_{p}=1.96$$

$$k_{p}=-1.03$$

## ejercicio #2
Tenemos la siguiente funcion de trasnferencia y se necesita que el sistema sea criticamente amortiguado:

$$G(s)=\frac{1}{s^{2}+6s+25}$$

Planteamos la respuesta del sistema en lazo abierto:

$$w_{n}=\sqrt{25}=5$$

$$2\zeta w_{n}=2\zeta 5=6$$

$$\zeta=\frac{6}{10}=0.6$$

Respuesta del sistema actualmente sub-amortiguada

Planteamos la ecuacion del controlador:

$$G_{o}(s)=\frac{k_{p}\frac{1}{s^{2}+6s+25}}{1+K_{p}\frac{1}{s^{2}+6s+25}}$$

Resolviendo la ecuacion tenemos:

$$G_{o}(s)=\frac{k_{p}}{s^{2}+6s+25+k_{p}}$$

Con esto empezamos a calcular el valor del controlador poniendo el valor de z como 1:

$$2\zeta w_{n}=2\cdot 1\cdot \sqrt{25+k_{p}}=6$$

$$(\sqrt{25+k_{p}})^{2}=3^{2}$$

$$25+k_{p}=9$$

$$k_{p}=9-25=-16$$
