En la [[Paradigma funcional|programación funcional]] fold es la operacion estandar que encapsula el patron de [[Esquemas de recursion#Recursion estructural|recursion estructural]].

# foldr para listas
```
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr f z [] = z
foldr f z (x : xs) = f x (foldr f z xs)
```

# Propiedad universal del fold
$$
\text{g = fold f b} \iff
\begin{cases}
\text{g [] = v} \\
\text{g (x : xs) = f x (g xs)}
\end{cases}
$$
La principal aplicacion de la propiedad universal del fold es como principio de demostracion que nos evita la necesidad de puebas inductivas.

# Propiedad de fusion del fold
$$
\text{h . fold g w = fold f v}
$$
