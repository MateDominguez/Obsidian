Operaciones aritmeticas y logicas en base 2. Todas las operaciones estan asociadas a un algoritmo de resolucion.
### Logical OR
$a \lor b = c$
bit a bit: $c_{i} = a_i \lor b_{i}$
coloquialmente: A o B
### Logical AND
$a \land b = c$
Bit a bit: $c_{i} = a_i \land b_{i}$
Coloquialmente: A y B
### Logical XOR
$a \oplus b = c$
Bit a bit: $c_{i}=(a_{i}\land \neg b_{i})\lor(\neg a_{i}\land b_{i})$
Coloquialmente: o A o B
### Logical NOT
$\neg a=c$
Bit a bit: $c_{i}=\neg a_{i}$
Coloquialmente: no A
### Left logical/arithmetical shift
Se desplazan los bits $n$ posiciones a la izquierda.
$a \ll n = c$ 
Bit a bit con $k$ bits: 
$$
c_{i} = 
\begin{cases}
a_{i-n} & \text{si}  & i \leq k-n-1 \\
0  & \text{si} & i>k=n=1
\end{cases}
$$

### Right logical shift
Se desplazan los bits $n$ posiciones a la derecha.
$a \gg_{l} n = c$ 
Bit a bit con $k$ bits: 
$$
c_{i} = 
\begin{cases}
a_{i+n} & \text{si}  & i \geq n \\
0  & \text{si} & i < n
\end{cases}
$$
### Right arithmetical shift
Se desplazan los bits $n$ posiciones a la derecha, copiando el valor del bit más significativo en las posiciones liberadas.
$a \gg_{a}n=c$
Bit a bit con $k$ bits: 
$$
c_{i} = 
\begin{cases}
a_{i+n} & \text{si}  & i \geq n \\
a_{k-1}  & \text{si} & i < n
\end{cases}
$$
### Adición binaria
$a + b = s$
La adición binaria para dos números $a$ y $b$ de $n$ digitos queda definida de la siguiente manera:
$$
\begin{cases}
c_{0}=0 \\
s_{i}=a_{i}\oplus b_{i}\oplus c_{i} & \text{para }0\leq i<n, \\
c_{i+1}=(a_{i}\land b_{i})\lor(a_{i}\land c_{i})\lor(c_{i}\land c_{i}) & \text{para }0\leq i<n, \\
s_{n}=c_{n}
\end{cases}
$$
#### Carry
El carry es un indicador de desborde de la operacion, cuando el resultado no es representable en $n$ bits.

#### [[Representacion de la informacion#Overflow|Overflow]] en la suma
Sea la suma de dos numeros $a$ y $b$, con carry $c$, decimos que:
$$
overflow \iff ((a_{n-1}=b_{n-1}) \land(a_{n-1}\neq c_{n-1}))
$$
