El algoritmo de Bellman-Ford resuelve, utilizando la tecnica de [[Programación Dinámica|programacion dinamica]], el [[Camino minimo en digrafos#Camino minimo con unico origen y multiples destinos|problema de camino minimo con unico origen]] en el caso general donde **los pesos pueden ser negativos**. 
Dado un digrafo pesado $G=(V,E)$ con un vertice de origen $s$ y una funcion $w:E\to R$, el algoritmo de Bellman-Ford **devuelve un valor booleano** indicando si hay o no un ciclo negativo que es alcanzable desde el origen. Si hay dicho ciclo, el algoritmo indica que no existe solucion. Si no hay ciclo, el algoritmo **produce los caminos minimos y sus pesos**.

El procedimiento $Bellman-Ford$ relaja vertices, progresivamente descreciendo un estimativo $v.d$ del peso del camino minimo desde el origen $s$ a cada vertice $v\in V$ hasta que alcanza el peso del camino minimo real $\delta(s,v)$. El algoritmo devuelde True si y solo si el grafo no contiene ciclos negativos alcanzables desde el origen.
```
Bellman-Ford(G,w,s)
	Inicializar-Unico-Origen(G,s) // O(V)
	
	repetir |G.V|-1 veces // O(V)
		para cada arista (u,v) en G.E // O(V + E)
			Relax(u,v,w)
			
	para cada (u,v) en G.E // O(E)
		si v.d > u.d + w(u,v)
			return False
			
	return True
V + V()
```
Despues de inicializar $d$ y $pred$, el algotimo hace $|V|-1$ pasadas sobre las aristas del grafo. Cada pasada es una iteracion del fo doble y consiste en relajar a cada arista del grafo una vez. Despues de hacer $|V|-1$ pasadas, el segundo for checkea si hay ciclos con pesos negativos y devuelve el valor booleano corespondiente.

![[Pasted image 20250421012358.png|]]
El algoritmo de Bellman-Ford tiene una complejidad temporal de $O(V^2+VE)$ si el grafo esta representado con listas de adyacencia. La inicializacion toma $$