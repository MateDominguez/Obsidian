# Ejercicios en clase
### Problema del CD ([[Backtracking|BT]])
Tenemos $P$ minutos de espacio en el disco.
Tenemos $N$ canciones que ocupan $P_{i}$ minutos con $1\leq i\leq N$.
Queremos llenar la mayor cantidad de minutos posibles.

Sol:
Soluciones candidatas con $N$ canciones: $Partes(N) = 2^N$ 
$$
CD(P_{1}\dots P_{N},k) = 
\begin{cases}
0 & \text{si } N=0,k \geq 0 \\
-\infty & \text{si } N=0, k \leq 0 \\
max \begin{cases}
CD(P_{1}\dots P_{N-1},k-P_{N})+P_{N} \\
CD(P_{1}\dots P_{N-1},k)
\end{cases}  & \text{Caso contrario}
\end{cases}
$$
Donde $P_{1}\dots P_{N}$ son las canciones a agregar y $k$ es el espacio restante.

Rta: $CD(P_{1}\dots P_{N},P)$
Complejidad del llamado recursivo: $\theta(2^N)$
Complejidad de evaluar la funcion: $O(1)$
Complejidad:$O(2^N)$

### Rod cutting ([[Programación Dinámica|PD]])
Tenemos una barra de tamano $n$ que podemos partir en barras de igual o menor taman, una lista de precios $P$ segun el tamano de la barra y queremos maximizar la ganancia.

Caso base: $Ganancia[0]=0$
Transicion: $Ganancia[i]=max(P_{i}+Ganancia[n-i]),1\leq i\leq n$.

Top-Down 

Sin memoizacion
```
def rod_cutting(n,P):
	if n==0:
		return 0

	ganancias = [0]*n
	for i in range(i,n+1):
		ganancias[i-1] = P[i] + rod_cutting(n-1,P)

	return max(ganancias)
```

Con memoizacion
```
def rod_cutting(n,P):
	memo = []
	
	if n==0:
		return 0

	if n in memo:
		return memo[n]

	ganancias = [0]*n
	for i in range(i,n+1):
		ganancias[i-1] = P[i] + rod_cutting(n-1,P)

	memo[n] = max(ganancias) 
	return max(ganancias)
```

Bottom-Up
```
def rod_cutting(n,P):
	memo = [0]*(n+1)

	for i in range(1,n+1):
		ganancias = [0]*i
		ganancias[0] = P[i]
		
		for j in range(1,i):
			ganancias[j] = P[i] + memo[i-j]
		
		memo[i] = max(ganancias)
```


### Coin change
Dada una cantidad objetivo de dinero $co$ y una lista de denominaciones de monedas $D$. Se busca la menor cantidad de monedas $CC$ de alguna denominacion de la lista que sumen a la cantidad deseada.

Estado -> Cantidad de monedas optima para una $co$
Transicion -> $CC(co) =min(CC(co+m))+1,\forall m\in D$

Sin memo
```
def cc(co,D):
	n = len(D)

	if co == 0:
		return 0

	vueltos = [0]*n

	for i in range(n):
		if D[i]<=co:
			vueltos[i] = cc(co-D[i],D)+1
		else:
			vueltos[i] = inf
			
	minimo = min(vueltos)

	return minimo
```

Con memo
```
memo = []
def cc(co,D):
	n = len(D)

	if co == 0:
		return 0

	if co in memo:
		return memo[co]

	vueltos = [0]*n

	for i in range(n):
		if D[i]<=co:
			vueltos[i] = cc(co-D[i],D)+1
		else:
			vueltos[i] = inf
			
	minimo = min(vueltos)

	memo[0] = minimo

	return minimo
```

---


# Practica 1: Tecnicas algoritmicas
## [[Backtracking]]
### Ejercicio 1: SumaSubconjuntosBT (Subsets)
a) $\{(0,0,0),(1,0,0),(0,1,0),(0,0,1),(1,1,0),(1,0,1),(0,1,1),(1,1,1)\}$
b) $\{(1,0,1),(0,1,0)\}$
c) $\{\{  \},(0),(1),(0,0),(1,0),(0,1),(1,1),(1,0,0),(0,1,0),(0,0,1),(1,1,0),(1,0,1),(0,1,1),(1,1,1)\}$
d) Sea $s =\sum_{i=1}^{n} a_{i}c_{i}$
![[Drawing 2025-03-26 16.14.09.excalidraw|100%]]

f) La complejidad es $2^{|C|}$ pues para cada llamada recursiva se crean dos ramas.

g) Diferencia entre arbol de backtracking y arbol de recursion? arbol de BT es correcto? ver punto $d$.
h) ![[Drawing 2025-03-26 23.41.00.excalidraw|100%]]
i) Redefino subset_sum agregandole un parametro $S$. Cuando llamo a la funcion le paso $\sum_{i=0}^{n-1}c_{i}$. Para cada llamada recursiva checkeo si $S$ es menor que $k$, de ser asi, retorna falso pues no importa cuantos elementos sume de $C$, nunca alcanzara a valer $k$. Ademas, en la llamada recursiva hago $S-C[i-1]$.

j)
```
subset_sum(C, i, j, a):
	Si j < 0
		retornar
	Si i = 0
		imprimir(a)
		retornar
	
	subet_sum(C,i-1,j,a)
	
	a[len(C)-i] = C[i]
	subet_sum(C,i-1,j-C[i-1],a)
```

### Ejercicio 2: MagiCuadrados (Permutations)
a)Para el primer cuadrado tenemos $n^2$ opciones, para el siguiente $n^2-1$ hasta completar el ultimo cuadrado donde nos quedara $1$ sola opcion ya que los numeros no se repiten, nos da un total de $n^2!$ combinaciones. Esta operacion se repite $n^2$ veces, una vez para cada cuadrado. La complejidad total es
$$
O\left( \sum_{i=0}^{n^2} \frac{n^2!}{(n^2-i)!} \right) = O(n^2!)
$$
b) 
```
MagiC(n):
	
	nums = set()
	for i in range(1,n**2+1):
		nums.add(i)

	M = []
	for i in range(n):
		M.append([])

	backtrack(M,i,j,nums):
		sum = 0
		
		if i == n and j == n:
			if esMagiC(M):
				return 1
			else:
				return 0
			
		if j == n:
			for n in nums:
				M[i+1,1] = n
				nums.remove(n)
				sum += Backtrack(M,i+1,1,nums)
				nums.add(n)
		else:
			for n in nums:
				M[i,j+1] = n
				nums.remove(n)
				sum += Backtrack(M,i,j+1,nums)
				nums.add(n)
				
		return sum

	return backtrack(M,0,0,nums)
```

![[Drawing 2025-03-27 17.50.46.excalidraw|100%]]

d) Podemos mejorar las podas si ademas checkeamos la suma parcial de las diagonales.
```
es_sol_parcial(M,i,j,n):
	suma_fila = 0
	for k in range(i):
		suma_fila += M[k,j]

	suma_col = 0
	for k in range(j+1):
		suma_col = M[i+1,k]

	// suma diag1 y diag 2

	return suma_fila <= n and suma_col <= n 
			and s_diag1 <= n and s_diag2 <= n
	
```

e) Tenemos $n$ filas, la suma de cada fila es el numero magico de orden $n$. 
La suma total de la matriz es
$$
\sum_{i=1}^{n^2}i=\frac{n^2(n^2+1)}{2}=\frac{n^4+n^2}{2}
$$
Si sabemos que cada fila vale lo mismo, podemos dividir la suma total por la cantidad de filas y obtendriamos el numero magico de orden $n$.
$$
\frac{n^4+n^2}{2}\times \frac{1}{n}=\frac{n(n^3+n)}{2}\times \frac{1}{n}= \frac{n^3+n}{2}
$$

$\therefore$  EL numero magico de orden $n$ es $\frac{n^3+n}{2}$.

### Ejercicio 3: MaxiSubconjunto (Combinations)
a)
```
MaxiS(conj,k,M):

	sols = []
	
	backtracking(conj,n,sol): // O((n k)*k)

		if n == 0: // leaf
			sols.append(sol.copy()) // O(k)
			return


		for num in conj.copy(): // O(1)
			conj.remove(num)
			sol.append(num)
			sols.append(backtracking(conj,n-1,sol))
			sol.pop()
			conj.add(num)

	backtracking(conj,k,[])

	suma_matriz(conj): // O(k^2)
		sum = 0
		for i in conj:
			for j in conj:
				sum += M[i,j]
		return sum

	sums = list(map(suma_matriz,sols)) // O((n k)*k^2)
	m = max(sums)
	
	return sums.index(m) 
	
```

b) Complejidad temporal:
Generamos todos los subconjuntos de tamaño 0 a $k$ a partir del conjunto de $n$ elementos. El numero de subconjuntos es
$$
\sum_{i=0}^{k}  \binom{n}{i}
$$

El numero de hojas es $\binom{n}{k}$. Ademas, para cada subconjunto de tamaño $k$ tenemos que calcular la suma matricial que tiene una complejidad de $k^2$. Por lo tanto la complejidad temporal es
$$
O(\sum_{i=0}^{k-1}  \binom{n}{i}+\binom{n}{k}\times k^2)
$$
Complejidad espacial:
Necesitamos guardar $\binom{n}{k}$ posibles soluciones, cada una con $k$ elementos.
Por lo tanto, la complejidad espacial es
$$
O(\binom{n}{k} \times k)
$$
c) Podemos calcular previamente una lista con los valores unicos presentes en al matriz y luego ordenarla de mayor a menor. Luego, nos quedamos con el k-esimo valor de la lista. Como queremos maximizar la suma de $\binom{k}{2}$ posiciones de la lista, queremos que las posiciones que tomamos tengan valores mayores a el valor k-esimo.

### Ejercicio 4: RutaMinima (Permutations)
a)
```
MagiC(D):
	n = len(D)
	nums = set()
	for i in range(1,n+1):
		nums.add(i)

	M = []
	for i in range(n):
		M.append([])

	sols = []
	
	backtrack(sol,nums)
		
		if len(nums == 0):
			return sol.copy() // O(n)
							
		for n in nums.copy(): // O(n)
			nums.remove(n)
			sol.append(n)
			sols.append(Backtrack(sol,nums))
			nums.add(n)
			sol.remove(n)
		
		return sols

	cuentaLoca(conj): // o(1)
	
	return min(map(cuentaLoca, backtrack(D)))
```
c)  

# Practica 3: Intro. a la teoria algoritmica de grafos

## Demostracion de propiedades simples sobre grafos

### Ejercicio 1: Equilibro Digrafo
$$
\begin{gather}
\text{Quiero probar que} \\
\sum_{v\in V(D)}d_{in}(v)=\sum_{v\in V(D)}d_{out}(v)=|E(D)| \\ \\
\text{Pruebo por induccion en $m$, siendo } m =|E(D)| \\
\text{Caso Base: } m=0 \to d_{out}(v) = d_{in}(v) =0\\
\text{Paso recursivo: }
\end{gather}
$$