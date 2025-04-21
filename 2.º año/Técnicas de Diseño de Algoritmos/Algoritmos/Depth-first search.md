---
aliases:
  - DFS
---
Dado un grafo, queremos recorrer sus vertices exactamente una vez.
El algoritmo explora el grafo en profundidad siempre que se pueda. Explora los vertices de la ultima arista $v$ descubierta. Una vez que se exploraron todos los vertices de $v$, "backtrackea" y explora los vertices que salen desde donde $v$ fue descubierta. Este proceso continua hasta que todos los vertices que son alcanzables desde el vertice original hayan sido descubiertos. Si queda algun vertice sin descubrir, la busqueda selecciona a uno de estos como el nuevo origen, repitiendo la busqueda desde ese origen. El algoritmo repite todo el proceso hasta haber descubierto cada vertice.

Cada vertice ese incialmente blanco, gris cuando es descubierto en la busqueda, y negro cuando esta completo, es decir, cuando su lista de adyacencia fue examinada completamente. 
Cada vertice tiene dos marcas temporales. La primera, $v.d$ registra cuando $v$ fue descubierto, y la segunda $v.f$ registra cuando la busqueda termino de examinar la dista de adyacencia de $v$.
```
blanco -> no visto
gris -> visto pero no completo (no vi todos sus hijos)
negro -> completo

DFS(G):
	para cada vertice u en G.V: // Om(V)
		u.color = blanco
		u.pred = null
		
	tiempo = 0

	para cada vertice u en G.V: // Om(V)
		si u.color == blanco
			busqueda(G,u)
	
busqueda(G,u):
	tiempo = tiempo + 1
	u.d = tiempo
	u.color = gris
	
	para cada vertice v en G.Adj[u]:
		si v.color == blanco:
			v.pred = u
			busqueda(G,v)

	tiempo = tiempo + 1
	u.f = tiempo
	u.color = negro
```
El resultado de depth-first search depende del orden en el que se recorren los vertices en el primer for de $DFS$ y del orden en que se visitan los vecinos de cada vertice en $busqueda$.

La complejidad de los for en $DFS$ toman $\Theta(V)$, sin incluir el tiempo que toma llamar a $busqueda$. El procedimiento $busqueda$ se llama una vez por cada vertice $v \in V$. Durante la ejecucion de $busqueda(G,s)$, el loop se ejecuta $|Adj[v]|$ veces.

La complejidad temporal de DFS es $\Theta(V+E)$. 
