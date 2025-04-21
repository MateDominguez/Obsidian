La tecnica de dividir y conquistar se basa en la descomposicion de un problema en subproblemas. Si un problema es demasiado dificil para resolverlo directamente, una alternativa es dividirlo en partes mas pequenas que sean mas faciles de resolver y luego uniendo todas las soluciones parciales obtener la solucion final. Es un caso particular de los [[algoritmos recursivos]].

Dado un problema a resolver para una entrada de tamano $n$, se divide la entrada en $r$ subprolemas. Estos subproblemas se resuelven de forma independiente y despues se combinan las soluciones para obtener  la solucion del problema original. En esta tecnical los subprolemas deben ser de la misma clase que el problema original, permitiendo una resolucion recursiva.

Se distinguen tres partes en un algoritmo dividir y conquistar:
* Una forma directa de resolver casos sencillos.
* Una forma de dividir el problema en 2 o mas subproblemas de menor tamano.
* Una forma de combinar las soluciones parciales para llegar a la solucion completa.

El esquema general es:
```
d&c(x)
	entrada: x
	salida: y

	si x es sufiecientemente facil entonces
		y <- calcular directamente
	sino
		descomponer x en instancias mas chicas x_1,..,x_r
		para i = 1 hasta r hacer
			y_i <= d&c(x_i)
		y <- combinat los y_i
	returnar y
	
```

La cantidad de subproblemas $r$, generalmente es chica $e$ dindependiente de la instancia particular que se resuelve. Para obtener un algoritmo eficiente, la medida de los subrproblemas debe ser simular y no necesitar resolver mas de una vez el mismo subproblema.