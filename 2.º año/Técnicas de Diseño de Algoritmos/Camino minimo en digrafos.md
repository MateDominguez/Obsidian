Dado un grafo $G=(V,E)$ queremos encontrar el camino minimo desde un vertice de origen dado $s \in V$ a cada otro vertice $v \in V$. 

El input a un problema de camino minimo es un digrafo pesado $G=(V,E)$, con una funcion de pesos $w:E\to \mathbb{R}$ que mapea aristas a pesos con valores reales. El **peso** $w(p)$ del camino $p=\langle v_{0},v_{1},\dots,v_{k} \rangle$ es la suma de los pesos de sus aristas constituyentes:
$w(p)=\sum_{i=1}^{k}w(v_{i-1},v_{i})$.

Se define el **peso del camino minimo** $\delta(u,v)$ desde $u$ a $v$ como:
$$
\delta(u,v)=
\begin{cases}
min\{w(p):u\to_{p}v\} & \text{si hay un camino desde $u$ a $v$}, \\
\infty & \text{c.c.}
\end{cases}
$$
El camino minimo desde el vertice $u$ al vertice $v$ es entonces definido como cualquier camino $p$ con peso $w(p)=\delta(u,v)$.

---
## Variantes
Dado un grafo $G$, se pueden definir tres variantes de problemas de caminos minimos:
1. **Unico origen - unico destino:** Determinar un camino minimo entre dos vertices especificos, $v$ y $u$.
2. **Unico origen - multiples destinos:** Determinar un camino minimo dedde un vertice especifico $v$ al resto de los vertices de $G$.
3. **Multiples origenes - multiples destinos:** Determinar un camino minimo entre todo par de vertices de $G$.

No se conocen algoritmos con mejor complejidad para el primer cado que para el segundo, alcanza con parar la ejecucion del algoritmo una vez que se alcanza el vertice de interes.

Generalmente, los algoritmos para resolver problemas de camino minimo se basan en que todo subcamino de un camino minimo entre dos vertices es un camino minimo.

---
## Propiedad de subestructura optima de un camino minimo
Dado un digrafo $G=(V,E)$ con una funcion de peso $l:E\to \mathbb{R}$, sea $P:v_{1}\dots v_{k}$ un camino minimo de $v_{1}$ a $v_{k}$. Entonces $\forall 1 \leq i\leq j\leq k$, $P_{v_{i}v_{j}}$ es un camino minimo desde $v_{i}$ a $v_{j}$.

Consideraciones:
**Aristas con peso negativo:**
* Si el digrafo $G$ no contiene ciclos de peso negativo o contiene alguno pero no es alcanzable desde $v$, entonces el problema sigue estando bien definido, aunque algunos caminos puedan tener longitud negativa.
* Sin embargo, si $G$ tiene algun ciclo con peso negativo alcanzable desde $v$, el concepto de camino de peso minimo deja de estar bien definido.
**Circuitos:**
* Siempre existe un camino minimo que no contenga circuitos (si el problema esta bien definido). No puede tener circuitos de longitud negativa porque pierde sentido la definicion de camino minimo. Tampoco puede tener ciclos de longitud posistiva, ya que sacando el ciclo obtenemos un camino de menor longitud.

---
### Representando caminos minimos
Dado un grafo $G=(V,E)$, mantener para cada vertice $v \in V$ un **predecesor** $v.pred$ que es otro vertice o Nil. Los siguientes algoritmos establecen el atributo $pred$ de tal manera que la cadena de predecesores que se origina en $v$ recorre en reversa el camino minimo desde $s$ a $v$. 

Dado un vertice $v$ tal que $v.pred \neq Nil$, el procedimiento $Imprimir-Camino(G,s,v)$ imprime el camino minimo desde $s$ a $v$.
```
Imprimir-Camino(G,s,v)
	si v == s
		imprimir s
	si no v.pred == nil
		imprimir "no existe camino desde s a v"
	si no
		Imprimir-Camino(G,s,v.pred)
		imprimir v
```

---
### Relajacion
Para cada vertice $v \in V$, los algoritmos de camino minimo de unico origen mantienen un atributo $v.d$, el cual es una cota superior del peso del camino minimo desde el origen $s$ a $v$. Llamamos a $v.d$ el **estimador de camino minimo**. 

Para inicializar los estimadores de camino minimo y los predecesores. Se llama a $Inicializar-Unico-Origen$. Despues de la inicializacion tenemos $v.pred=Nil$, para todo $v\in V$, $s.d=0$ y $v.d=\infty$ para $v\in V-\{s\}$.
```
Inicializar-Unico-Origen(G,s)
para cada vertice v en G.V
	v.d = inf
	v.pred = Nil
s.d = 0
```

El proceso de **relajacion** de una arista $(u,v)$ consiste en testear si al pasar por el vertice $u$ mejoramos el camino minimo al vertice $v$ encontrado hasta ahora, de ser asi se actualiza $v.d$ y $v.pred$.
```
Relax(u,v,w)
si v.d > u.d + w(u,v)
	v.d = u.d + w(u,v)
	v.pred = u
```

---
## Camino minimo - Unico origen - multiples destinos
**Problema:** Dado $G=(V,E)$ un digrafo, $l:E\to \mathbb{R}$ una funcion que asigna a cada arco una longitud y $v \in V$ un vertice del digrafo. 
El objetivo es calcular los camino minimos desde $v$ al resto de los vertices. 

Distintas situaciones:
* El grafo puede ser oritentado o no.
* Todos los arcos tienen igual longitud o no.
* Todos los arcos tienen longitud negativa o no.
* Se asume que todo vertice es alcanzable desde $v$.

En el caso de tener todos los arcos igual longitud, el problema se traduce en encontar los caminos de minima cantidad de aristas.
Esto se resuelve con [[BFS]].

### Camino minimo - Unico origen - Grafo pesado
#### [[Dijkstra]]
#### [[Bellman-Ford]] 
