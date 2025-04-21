---
aliases:
  - Algoritmos greedy
  - Greedy
  - greedy
---

**Idea**: Construir una solucion seleccionando en cada paso **la mejor alternativa posible localmente** segun una funcion de seleccion, sin considerar las implicancias de esta seleccion.

* En cada etapa se toma la decision que parece mejor basandose en la informacion disponible en ese momento, sin tener en cuanta las consecuencias futuras.

* Una decision tomada nunca es revisada y no se evaluan alternativas, esto los hace muy eficientes.

* Faciles de inventar e implementar, generalmente eficientes.

* No funcionan para todos los problemas, estos no pueden ser resueltos con este enfoque.
	* Proporcionan [[Algoritmos heuristicos|heuristicas]] sencillas para [[problemas de optimizacion]].
	* Permiten construir soluciones razonables, pero sub-optimas.

* Funcion de seleccion.