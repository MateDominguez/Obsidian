### Introduccion
**Idea:** Recorrer sistematicamente todas las posibles configuraciones del espacio de soluciones de manera recursiva.

Puede usarse tanto para problemas de optimizacion como de factibilidad.

Backtracking es una modificacion de [[Fuerza bruta|fuerza bruta]] que aprovecha propiedades del problema para evitar analizar todas las configuraciones. 

---
### Soluciones
**Soluciones parciales:** Estados intermedios durante la ejecicion del algoritmo que representan las deciciones todamas hasta el momento, no constituyen una solucion completa al problema.

**Soluciones candidatas:** Son extensiones potenciales de una solucion parcial, representan las diferentes opciones o caminos que podemos tomar desde el estado actual.

**Soluciones validas:** Son las soluciones que cumplen con la condicion deseada y que representan una solucion completa.

---
### Construccion de una solucion
* Utiliza un vector $a =(a_{1},a_{2},\dots,a_{n})$ para representar una solucion candidata, cada $a_{i}$ pertenece a un dominio/conjunto finito $A_{i}$.

* El espacio de soluciones es el producto cartesiano $A_{i}\times\dots \times A_{n}$.

* En cada paso se extienden las soluciones parciales $a =(a_{1},a_{2},\dots,a_{k}),k<n$ agregando un elemento mas, $a_{k+1}\in S_{k+1}\subseteq A_{k+1}$ al final del vector $a$.

* Las soluciones parciales son sucesoras de la anterior.

* Si el conjunto de soluciones sucesoras es vacio, esa rama no se continua explorando.

---

### Arbol de backtracking
Se puede pensar el espacio de busqueda como un arbol dirigido, donde cada vertice representa una solucion parcial. 

Un vertice $x$ es hijo de $y$ si la solucion parcial $x$ se puede extender desde la solucion parcial $y$. 

La raiz del arbol se corresponde con la solucion parcial vacia.

---

### Backtrack
El proceso de backtracking recorre el arbol en profundidad. 
Cuando podemos deducir que una solucion parcial no conducira a una solucion valida, no es necesario seguir explorando esa rama del arbol de busqueda, entonces se "poda" el arbol y se retrocede (backtrack) hasta encontrar un vertice con un hijo sin explorar.

---
### Podas
Una poda puede ser por:
* **Factibilidad:** Ninguna extension de la solucion parcial derivara en una solucion valida del problema.
* **Optimalidad** (problemas de optimizacion): Ninguna extension de la solucion parcial derivara en una solucion optima del problema.

Para poder aplicar la poda por factibilidad, la represetacion debe cumplir que si una solucion parcial $a$ no cumple con las propiedades deseadas, tampoco lo hara cualquier extension posible de ella.

---

### Esquema general
#### Todas las soluciones
```
BT(a,k)

if k == n + 1:
	procesar(a)
	return
else:
	for a' in sucesores(a,k):
		BT(a',k+1)

return
```

#### Una solucion
`sol` variable global, `encontro` variable booleana global.
```
BT(a,k)

if k == n + 1:
	sol = a
	encontro = True
else:
	for a' in sucesores(a,k):
		BT(a',k+1)
		if encontro:
			return sol

return
```
