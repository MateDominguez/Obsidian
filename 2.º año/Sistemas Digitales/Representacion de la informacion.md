## Objetivo
Representar una magnitud a través de un sistema de representación.

**Sistema de representación:**
* **Finito**: Cantidad acotada de elementos por restricciones implementativas.
* **Composicional**: Magnitudes son representadas por una serie de elementos atómicos.
* **Posicional**: La posición de cada dígito determina unívocamente la proporción en la que modifica el valor de la magnitud.

## Bases
Una base determina la cantidad de símbolos distintos que puede tomar un dígito.
Cantidad de dígitos de una magnitud $N$ en la base $X$ =  $\log_{X}(N)$.
### Cambio de base
El cambio de base es una operación que transforma un número N representado como una lista de símbolos en una base y lo representa en otra base.
#### Teorema de la división
Para todo $a, b \in \mathbb{Z}$ con $b \neq 0$, existen únicos enteros $q$ (cociente) y $r$ (resto) tales que:
*  $a = b \times q + r$ 
*  $0 \leq r < |b|$

**Aplicación al cambio de base**: Para convertir un número decimal $a$ a base $b$:
- Divide $a$ entre $b$ $\to$ obtienes $q_{1}$​ y $r_{1}$​
- Divide $q_{1}$​ entre $b$ → obtienes $q_{2}$​ y $r_{2}$​
- Continúa dividiendo hasta que $q_{n} = 0$​
El número en base $b$ será: $(r_{n}r_{n-1}\dots r_{2}r_{1})_{b}$

## Rango de representación
En un soporte electronico, cada dato se representa con una cantidad finita de elementos.
El rango de representacion viene asociado al tipo de dato. El rango de valores para una tira de $K$ digitos en la base $X$ es = $X^K$
### Overflow
Decimos que hay overflow cuando una magnitud cae fuera del rango de representacion.

## Datos
Los datos tienen **información asociada** y el **tipo de dato**.
La **información asociada** son los valores de cada dígito. El **tipo de dato** nos indica como interpretar la información.
### Tipos numéricos en base 2
* **Sin signo:** Representan números positivos.
* **Signo + Magnitud:** Se usa el primer bit para representar el signo de la magnitud. $0$ positivo, $1$ negativo.
* **Exceso m:** Represento $n$ como $m + n$. Estamos desplazando la magnitud asociada al cero, los valores a la izquierda de $m$ son interpretados como negativos.
* **Complemento a 2**
	* Los positivos se representan igual.
	* Negativos:
		Método 1: Invertir los $K$ bits y sumar uno.
		Método 2: $2^K_{(10)} -n$ 