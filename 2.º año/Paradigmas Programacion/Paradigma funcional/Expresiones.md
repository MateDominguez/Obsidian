Las expresiones son secuencias de símbolos que sirven para representar datos, funciones y funciones aplicadas a datos.

Una expresión puede ser:
* Un **constructor:** 
	* `True False [] (:) 0 1 2 …`
* Una **variable**: 
	* `longitud ordenar x xs (+) …` 
* La **aplicación** de una expresión a otra:
	* `ordenar lista`
	* `not True`
	* `(+) 1`

La aplicación es asociativa a izquierda
`f x y = (f x) y`

La `->` es asociativa a derecha
`a -> b -> c = a -> (b -> c)`

### Polimorfismos
Hay expresiones que pueden tomar más de un tipo, estos son [[Polimorfismo|polimorfismos]]. Usamos variables de tipo `a, b, c` para denotar tipos desconocidos.
Ej.: `id :: a -> a` 

### Evualuacion
Evualuar una expresion consiste en:
* Buscar la subexpresion mas externa que coincida con el lado izquierdo de una ecuacion.
* Reemplazar la subexpresion que coincide con el lado izquierdo de la ecuacion por la expresion correspondiente al lado derecho.
* Continuar evaluando la expresion resultante.

La evaluacion se detiene cuando se da uno de los siguientes casos:
* La expresión es un [[Constructor|constructor]] o un constructor aplicado.
* La expresion es una [[Funcion|funcion]] parcialmente aplicada.
* Se alcanza un estado de error.
