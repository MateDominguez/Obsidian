# Practica 1
### Ejercicio 10
Caso $x$ positivo.
Si $x$ es positivo y $signExt_{n}(x)$ es $x$ + $n$ ceros. Estos representan el mismo numero en complemento a 2.

Caso $x$ negativo.
Si $x$ es negativo y $signExt_{n}(x)$ es $x$ + $n$ unos. Primero negamos ambos numeros bit a bit y luego le sumamos 1, para poder asi interpretar el numero negativo. El numero obtenido es el mismo, a diferencia de los ceros. Por lo tanto, representan el mismo numero.

### Ejercicio 11
2  -> 0010
-5 -> 1011
0  -> 0000

a)
1101 -> -3
0100 -> 4
1111 -> -1

b) Sea $x$ la representacion de un numero en complemento a 2. El inverso aditivo de $x$ se calula de la siguiente manera: Inviertir los bits y sumar 1.

### Ejercicio 12
Supongamos que dicho sistema existe.
Queremos un sistema que tenga un representacion para el cero y la misma cantidad de numeros positivos y negativos representados. Por lo tanto, la cantidad total de numeros que queremos representar es: $1 + 2n$. 

Al mismo sabemos que el rango de representacion es $2^k$, ya que el sistema representa numeros como cadenas binarias de longitud fija $k$. 

Por ultimo, se nos pide que el sistema sea biyectivo, es decir no admite mas de una representacion para cada numero y toda cadena disponible es utilizada para representar algun numero. 

Para que el sistema sea biyectivo necesitamos que $2^k=1+2n$. Como $2n + 1$ es siempre impar y $2^k$ es par para todo $k>0$, entonces la igualdad no se cumple.

Por lo tanto podemos concluir que la afirmacion es verdadera.

### Ejercicio 13
Asumiendo que va a haber una doble representacion para el 0. Un ejemplo de un sistema de representacion biyectivo con misma cantidad de numeros positivos y negativos representados es Signo + Magnitud

# Practica 2
## Circuitos Combinatorios
### Ejercicio 1
a) 
$$
\begin{matrix}
x.z=(x+y).(x+\bar{y}).(\bar{x}+z) \\
x.z=x+(y.\bar{y}).(\bar{x}+z) \\
x.z=x+0.(\bar{x}+z) \\

\end{matrix}
$$ 
