---
tags:
  - tipo-recursivo
---
Se pueden expresar como [[Tipos Algebraicos|tipo recursivo]] de la siguiente manera:
```hs
data Arbol a = Hoja a | Nodo a (Arbol a) (Arbol a)
```

Algunas funciones con [[recursion estructural]]:

Cuanta el total de hojas que tiene un arbol
```hs
hojas :: Arbol a -> Int
hojas (Hoja x) = 1
hojas (Nodo x i d) = hojas i + hojas d
```

Mide la altura de un árbol
```hs
altura :: Arbol a -> Int
altura (Hoja x) = 0
altura (Nodo x i d) = 1 + (altura i `max` altura d)
```
