# Error en Estado Estacionario

Daniel Felipe Ladino, Angel David Melo

El **error en estado estacionario** es un concepto crucial en el estudio de sistemas de control. Representa la diferencia persistente entre la salida deseada (la entrada de referencia) y la salida real del sistema, una vez que toda la dinámica transitoria inicial ha desaparecido y el sistema ha alcanzado un comportamiento estable a largo plazo.

Un ejemplo es imaginar querer que un robot siga una línea recta perfecta. El error en estado estacionario sería qué tan lejos de la línea recta termina el robot después de un tiempo largo. Un error pequeño significa alta precisión.

Matemáticamente, si $r(t)$ es la entrada de referencia y $y(t)$ es la salida, el error en el tiempo es $e(t) = r(t) - y(t)$. El error en estado estacionario, $e_{ss}$, es el valor de este error cuando el tiempo tiende a infinito:

$$e_{ss} = \lim_{t \to \infty} e(t)$$

## 1. Calculando el Error Final

Para calcular $e_{ss}$ sin tener que analizar la respuesta en el tiempo hasta el infinito, utilizamos una herramienta poderosa del dominio de Laplace: el Teorema del Valor Final.

Este teorema nos permite encontrar el valor final en el tiempo de una función si conocemos su transformada de Laplace. Aplicándolo a la función de error $e(t)$, cuya transformada es $E(s)$, obtenemos la fórmula clave para el error en estado estacionario:

$$e_{ss} = \lim_{s\rightarrow0}sE(s)$$

La función de error en el dominio de Laplace, $E(s)$, para un sistema de control realimentado unitario (donde la salida se resta directamente a la entrada) con una función de transferencia en lazo abierto $G(s)$, se relaciona con la entrada de referencia $R(s)$ mediante la siguiente expresión:

$$E(s) = \frac{R(s)}{1 + G(s)}$$

Combinando estas dos fórmulas, obtenemos la expresión general para calcular el error de estado estacionario para cualquier entrada $R(s)$:

$$e_{ss} = \lim_{s\rightarrow0}s \left( \frac{R(s)}{1 + G(s)} \right)$$

## 2. Error para Entradas Comunes (Escalón, Rampa, Parábola)

La magnitud del error en estado estacionario depende fundamentalmente del tipo de señal de entrada que se aplica al sistema. Las entradas más comunes que usamos para probar los sistemas son el escalón, la rampa y la parábola.

1.  **Entrada Escalón Unitario:** Representa una demanda de posición constante ( $r(t) = u(t)$ ). Su transformada es $R(s) = 1/s$. Sustituyendo en la fórmula general del error:
    $$e_{escalon} = \lim_{s\rightarrow0} \frac{1}{1 + G(s)} = \frac{1}{1 + G(0)}$$
    Este error se llama **Error de Posición ($E_{ssp}$)**.

2.  **Entrada Rampa Unitario:** Representa una demanda de velocidad constante ( $r(t) = t \cdot u(t)$ ). Su transformada es $R(s) = 1/s^2$. Sustituyendo:
    $$e_{rampa} = \lim_{s\rightarrow0} \frac{1}{sG(s)}$$
    Este error se llama **Error de Velocidad ( $E_{SSv}$ )**.

3.  **Entrada Parábola Unitario:** Representa una demanda de aceleración constante ( $r(t) = \frac{1}{2}t^2 \cdot u(t)$ ). Su transformada es $R(s) = 1/s^3$. Sustituyendo:
    $$e_{parabola} = \lim_{s\rightarrow0} \frac{1}{s^2G(s)}$$
    Este error se llama **Error de Aceleración ($E_{ssa}$)**.

## 3. Tipos de Sistemas (Clasificación por "Integradores")

La capacidad de un sistema para tener un error en estado estacionario finito o cero para estas entradas estándar está determinada por una característica de su función $G(s)$: el número de polos que tiene en el origen ($s=0$). A esto le llamamos el **Tipo del Sistema**.

>🔑 **Tipo de Sistema:** Es el número de polos de $G(s)$ que están exactamente en $s=0$. Cada polo en $s=0$ corresponde a un "integrador" en el sistema, que ayuda a reducir el error acumulado.

La relación entre el Tipo de sistema y el error para las entradas estándar es la siguiente:

| Sistema | $E_{ssp}$ (Escalón) | $E_{SSv}$ (Rampa) | $E_{ssa}$ (Parábola) | Descripción                      |
|---------|---------------------|-------------------|----------------------|----------------------------------|
| Tipo 0  | $k$ (finito)        | $\infty$        | $\infty$         | Ningún polo en $s=0$       |
| Tipo 1  | $0$                 | $k$ (finito)      | $\infty$         | Un polo en $s=0$         |
| Tipo 2  | $0$                 | $0$             | $k$ (finito)       | Dos polos en $s=0$       |

*Donde* $k$ *es un valor finito distinto de cero.*

Esto significa que un sistema Tipo 0 puede seguir una posición (escalón) con un error constante, pero no puede seguir una velocidad o aceleración constante sin que el error se vaya a infinito. Un sistema Tipo 1 puede seguir una posición sin error, una velocidad con error constante, pero no una aceleración. Un Tipo 2 puede seguir posición y velocidad sin error, y una aceleración con error constante.

💡**Ejemplo Corto:** Si $G(s) = \frac{10(s+2)}{s(s+1)(s+3)}$, como tiene un factor $s$ en el denominador, es Tipo 1. Según la tabla, esperaríamos error 0 para escalón, finito para rampa e infinito para parábola. Esto se verifica al calcular los límites correspondientes.

## 4. Influencia de los Controladores (Ej. Proporcional $K_p$)

Podemos usar controladores para modificar $G(s)$ y así afectar el error en estado estacionario. Un controlador proporcional ($K_p$) simplemente multiplica $G(s)$ por una constante, resultando en una nueva función en lazo abierto $G_{ol}(s) = K_p G(s)$.

Para un sistema Tipo 0, el error de escalón es $e_{escalon} = \frac{1}{1 + G_{ol}(0)} = \frac{1}{1 + K_p G(0)}$. Aumentar la ganancia $K_p$ puede *reducir* este error, pero no lo hace cero a menos que $K_p$ sea infinito.

Para lograr error cero para rampas, parábolas, o eliminar completamente el error de escalón en sistemas Tipo 0, a menudo se necesita añadir *acción integral* al controlador (como en un controlador PI o PID), lo cual, en esencia, introduce un polo en el origen en la función de transferencia en lazo abierto, aumentando así el Tipo del sistema efectivo.

## 5. Sensibilidad: Robustez ante Cambios

La **sensibilidad** es otra métrica importante. Nos dice cuánto se verá afectado el rendimiento de nuestro sistema (por ejemplo, su función de transferencia o su error) si uno de los parámetros de la planta ( $G(s)$ ) cambia un poco. Un buen diseño de control busca que el sistema en lazo cerrado sea poco sensible a estas variaciones de la planta.

La fórmula general para la sensibilidad de una función $F$ con respecto a un parámetro $P$ es:
$$S_{F:P} = \frac{P}{F} \frac{\partial F}{\partial P}$$
Un valor bajo de sensibilidad indica que la función $F$ es robusta ante cambios en el parámetro $P$.

## 6. Conclusiones

* El error en estado estacionario mide la precisión final de seguimiento.
* Se calcula usando el Teorema del Valor Final y la función $G(s)$.
* Su valor (cero, finito, infinito) depende crucialmente del **Tipo del sistema**, que es el número de integradores (polos en $s=0$) en $G(s)$, y del tipo de **entrada** (escalón, rampa, parábola).
* Los controladores pueden modificar el Tipo o la ganancia de $G(s)$ para reducir o eliminar el error. La acción integral es clave para lograr error cero con entradas de mayor orden o en sistemas Tipo 0.
* Un buen diseño busca minimizar el error y hacer el sistema poco sensible a cambios en la planta.
