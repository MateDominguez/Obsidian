Los grafos sirven para modelar relaciones entre entidades.

---
## Definiciones
### Grafo
Un **grafo** $G=(V,E)$ es un par de conjuntos, donde $V$ es un conjunto de **nodos** o **vertices** y $E$ es un subconjunto del conjunto de pares **no ordenados** de elementos distintos de $V$. Los elementos de $E$ se llaman **aristas**.
Ademas, $n_{G}=|V|,~m_{G}=|E|$

### Vecindad
Dados $v$ y $w\in V$, si $e = (v,w) \in E$ se dice que $v$ y $w$ son **adyacentes** y que $e$ es **incidente** a $v$ y $w$.

La vecindad de un vertice $v,~N(v)$, es el conjunto de los vertices adyacentes a v. Es decir: $$N(v)={w\in V:(v,w)\in E}$$
#### Adyacencia
Un nodo es adyacente a otro si estan conectados.
#### Incidencia
Una arista es incidente a un nodo si conecta dicho nodo con algun otro.

### Multigrafo
Un multigrafo es un grafo en el que puede haber varias aristas entre el mismo par de vertices distintos. $E$ pasa a ser un multiconjunto de aristas.
### Pseudografo
Un pseudografo es un grafo en el que puede haber varias aristas entre cada par de vertices y tambien puede haber aristas que unan a un vertise con si mismo.
### Grafo dirigido / Digrafo
Un digrafo $G=(V,E)$ es un par de conjuntos $V$ y $E$ donde $V$ es el conjunto de nodos o vertices  y $E$ es un subconjunto del conjunto de los pares **ordenados** de elementos distintos de $V$, los elementos de $E$ se llaman **arcos**.
### Grafo pesado
Grafo $G=(V,E,w)$ con $w(e)$ una funcion de pesos que asigna a cada arista $e=(u,v)$ un peso.
### Grafo completo
Un grafo se dice completo si todos sus vertices son adyacentes entre si. Notaremos $K_{n}$ a grafo completo de $n$ vertices.

### Grado
El grado de un vertice $v$ en el grafo $G, d_{g}(v)$ es la cantidad de aristas incidentes a $v$ en $G$.
$\delta(G)$ es el grado minimo de $G$ y $\Delta(G)$ es el grado maximo de $G$.

 **Teorema:** Dado un grafo $G=(V,E)$, la **suma de los grados** de sus vertices es igual a 2 veces el numero de aristas. Es decir,
$$
\sum_{v\in V}d(v)=2m
$$
### Recorrido
Un recorrido es una sucesion de vertices y aristas de un grafo, tal que $e_{i}$ sea inncidente a $v_{i-1}$ y $v_{i}$ para todo $i=1\dots k :P=v_{0}e_{1}v_{1}..e_{k}v_{k}$.
### Camino
Un recorrido es un recorrido que no pasa dos veces por el mismo vertice.
### Circuito
Un circuito es un recorrido que empieza y termina en el mismo vertice.
#### Circuito euleriano
Un circuito euleriano es un ciclo en un grafo finito que recorre cada **arista** exactamente una vez.
#### Circuito hamiltoniano
Un circuito hamiltoniano es un ciclo en un grafo que recorre cada **vertice** exactamente una vez.
### Ciclo o circuito simple
Un ciclo es un circuito (de tres o mas vertices) que no repite vertices. 

### Longitud
Dado un recorrido $P$, su longitud, $l(P)$ es la cantidad de aristas que tiene.
### Distancia entre dos vertices
La distancia entre dos vertices $u$ y $v$ se define como la longitud del camino mas corto entre $v$ y $w$, $d(v,w)$.

Si no existe recorrido entre $v$ y $w$ se define la distancia como infinito, $d(v,w)=\infty$.
La distancia de un vertice consigo mismo es $0$, $d(u,u)=0$. 

---
## Representacion
Se puede elegir entre dos maneras de representar a un grafo $G=(V,E)$. Ambas representaciones son validas tanto para grafos dirigidos como no dirigidos.
#### Lista de adyacencia
La representacion por lista de adyacencia de un grafo $G(V,E)$ consiste en un array $A$ con $|V|$ cantidad de listas, una por cada vertice en $V$. Para cada $u \in V$, $A[u]$ contiene todos los vertices $v$ tal que hay una arista $(u,v)$. Figura (b).

* Opcion preferida para grafos dispersos, donde $|E|$ es mucho menor que $|V|^2$.
* Si $G$ es un grafo dirigido, la suma de las longitudes de todas las listas de aydacencia es $|E|$.
* Si $G$ es un grafo no dirigido, la suma de las longitudes de todas las listas de aydacencia es $2|E|$.
* Es robusta y permite representar distintos tipos de grafos.
* No proporciona una manera rapida de determinar si una arista esta presente en el grafo.

Complejidad espacial: $\Theta(V+E)$
La complejidad de encontrar cada vertice en el grafo tambien toma $\Theta(V+E)$ ya que hay que mirar todas las listas en $|V|$. 
Si $|E|=\Omega(V)$, como en un grafo no dirigido conexo o en un grafo digido altamente conexo, entonces encontrar cada vertice toma $\Theta(E)$.

#### Matriz de adyacencia
La representacion por matriz de adyacencia de un grafo $G(V,E)$ consiste de una matriz $A=(a_{ij})$ de tamaño $|V|\times|V|$ tal que 
$$
a_{ij}=
\begin{cases}
1 & \text{si } (i,j)\in E \\
0 & \text{caso contrario}
\end{cases}
$$
Figura (c)

* Opcion preferida para grafos densos, donde $|E|$ es cercano a $|V|^2$ o cuando se necesita determinar si dos vertices estan conectados en $O(1)$.

Complejidad espacial: $\Theta(V^2)$

![[Pasted image 20250331112411.png|Grafo no dirigiro con sus  distintas representaciones]]
> [!obs] Observacion
> Aunque la representacion por lista de adyacencia es asintoticamente igual de eficiente en cuanto a complejidad espacial con respecto a la representacion por matriz de adyacencia, las matrices de adyacencia son mas simples y pueden ser preferibles para grafos relativamente chicos.
