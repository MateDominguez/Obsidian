# Esquemas de recursion sobre listas
## Recursion estructural
Sea `g :: [a] -> b` definida por dos ecuaciones:
```
g [] = (caso base)
g (x : xs) = (caso recursivo)
```

La definicion de `g` esta dada recursion estructural si:
* El caso base devuelve un valor fijo `z`.
* El caso recursivo se escribe usando `x` y `(g xs)`, pero sin usar el valor de `xs` ni otros llamados recursivos.

Toda recursion estructural es una instancia de foldr.
#### [[foldr]]
La funcion foldr abstrae el esquema de recursion estructural
```
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr f z [] = z
foldr f z (x : xs) = f x (foldr f z xs)
```

## Recursion primitiva
Sea `g :: [a] -> b` definida por dos ecuaciones:
```
g [] = (caso base)
g (x : xs) = (caso recursivo)
```

La definicion de `g` esta dada por recursion primitiva si:
* El caso base devuelve un valor fijo `z`.
* El caso recursivo se describe usando `x` , `g(xs)` y `xs`, pero sin hacer otros llamados recursivos.

Similar a la recursion estructural, pero permite referirse a xs.

Todas las definiciones dadas por recursion estructural tambien estan dadas por recursion primitiva. Por otro lado, hay definiciones dadas por recursion primitiva que no estan dadas por recursion estructural.

Toda recursion primitiva es una instancia de recr.
#### recr
La funcion recr abstrae el esquema de recursion primitiva:
```
recr :: (a -> [a] -> b -> b) -> b -> [a] -> b
recr f z [] = z
recr f z (x : xs) = f x xs (recr f z xs)
```

## Recursion iterativa
Sea `g :: [a] -> b` definida por dos ecuaciones:
```
g [] = (caso base)
g (x : xs) = (caso recursivo)
```

La definicion de `g` esta dada por recursion iterativa si:
* El caso base devuelve un acumulador `ac`.
* El caso recursivo invoca inmediatamente a `(g ac' xs)`, donde  `ac'` es el acumulador actualizado en funcion de su valor anterior y el valor de `x`.

Toda recursion iterativa es una instancia de foldl.
#### foldl
Toda recursion interativa es una instancia de foldl.
```
foldl :: (b -> a -> b) -> b -> [a] -> b
foldl f ac [] = ac
foldl f ac (x : xs) = foldl f (f ac x) xs
```

# Esquemas de recursion sobre otras estructuras
## Recursion estructural
La recursion extructural se generaliza a [[Tipos Algebraicos|tipos algebraicos]] en general.

Supongamos que `T` es un tipo algebraico. 
Sea `g :: T -> Y` definida por ecuaciones:
```
g(CBase_1 <parametros>) = <casobase_1>
...
g(CBase_n <parametros>) = <casobase_n>
g(CRecursivo_1 <parametros>) = <casorecursivo_1>
...
g(CRecursivo_m <parametros>) = <casorecursivo_m>
```

La definicion de `g` esta dada por recursion estructural si:
* Cada caso base se escribe combinando los parametros.
* Cada caso recursivo de escribe combinando:
	* Los parametros del constructor que no son de tipo `T`.
	* El llamado recursivo sobre cada parametro de tipo `T`.
	Pero:
	* Sin usar los parametros del constructor que son de tipo `T`.
	* Sin hacer otros llamados recursivos.