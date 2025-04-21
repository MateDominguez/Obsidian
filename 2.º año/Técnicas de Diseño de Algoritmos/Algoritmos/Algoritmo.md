Un **algoritmo** es un procedimiento para resolver un problema, descripto por una secuencia finita de pasos, que termina en un tiempo finito.

Debe estar formulado en termino de pasos sencillos que sean:
* Precisos: se debe indicar el orden de ejecucion de cada paso
* Bien definidos: en toda ejecucion del algoritmo se debe obtener el mismo resultado.
* Finitos: el algoritmo tiene que tener un numero determinado de pasos.

Un algoritmo siempre debe:
* Brindar una respuesta.
* Garantizar que termina.
* Ser descriprto de una manera clara y precisa.


# Complejidad
La complejidad de un agoritmo es una funcion que representa el tiempo de ejecucion en funcion del tamano de la entrada.

### Tiempo de ejecucion
Tiempo de ejecucion de un algoritmo $A$ para una instancia $I$ = $T_{A}(I)$.
* Para un $b$ fijo, si la entrada ocupa $m$ celdas: $|I|=b\times n=O(n)$
* Complejidad: $f_{A}(n)=max_{I:|I|=n}(T_{A}(I))$
