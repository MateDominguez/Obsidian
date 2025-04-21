Una funcion relaciona los valores en el dominio con los del codominio.
Una funcion en [[Haskell]] tiene un *input* y *output* y describe como producir el *output* con el *input*.

Las funciones son [[Ciudadano de primera clase|ciudadanos de primera clase]], lo que significa que:
* Se les puede asignar nombres.
* Pueden ser el valor de una [[Expresiones|expresion]].
* Pueden ser miembros de una lista/tupla.
* Pueden ser pasados como argumentos a una funcion.
* Pueden ser devueltos como resultado de una funcion.

Las 'funciones' son verdaderas funciones matemáticas (parciales o totales).
* Aplicar una función no tiene efectos secundarios.
* A una misma entrada corresponde siempre la misma salida.
* Las estructuras de datos son inmutables.

Las funciones se definen como un conjunto de ecuaciones.
El orden de las ecuaciones es relevante. Si hay varias ecuaciones que [[Pattern matching|coinciden]] se usa siempre la primera.

### Funciones de orden superior
Una funcion de alto superior es una funcion que toma a otras funciones como parametros o que devuelve una funcion como resultado.

### Funciones anonimas
#### Notacion lambda
Una expresion de la forma
$$
\backslash x  \to e
$$
representa una funcion que recibe un parametro $x$ y devuelve $e$.

### Currificacion


### Aplicacion parcial
Las funciones en [[Haskell]] siempre toman un unico argumento.