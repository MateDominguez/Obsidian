## Clase 00

```hs
factorial :: Int -> Int
factorial 0 = 1
factorial 1 = 1
factorial n = n * factorial (n - 1)
```

```hs
sumaN :: Int -> [Int] -> [Int]
sumaN k [] = []
sumaN k (x : xs) = (x + k) : sumaN k xs
```

```hs
aparece :: Eq a => a -> [a] -> Bool
aparece e [] = False
aparece e (x : xs) = if e == x then True else aparece e xs
```

```hs
-- Selection Sort
ordenar :: Ord a => [a] -> [a]
ordenar [] = []
ordenar (x:xs) = if minimo x xs then x : ordenar xs else ordenar xs ++ [x]

minimo :: Ord a => a -> [a] -> Bool
minimo _ [] = True
minimo x (y:ys) = if x < y then minimo x ys else False 
```

```hs
-- Intento de Merge Sort
ordenar :: [Int] -> [Int]
ordenar xs = (take (length xs / 2) xs) : split (drop (length xs / 2) xs) 

split :: [Int] -> [Int] -> [Int]
split [] = []
split [x] = sort [x]
split [x,y] = sort [x,y] 
split xs = split (take (length xs / 2) xs) : split (drop (length xs / 2) xs)

sort :: [Int] -> [Int] -> [Int]
ordenarAux xs _ = xs
ordenarAux _ ys = ys
ordenarAux (x : xs) (y : ys)
	| x < y = x : ordenarAux xs (y : ys)
	| otherwise = y : ordenarAux (x : xs) ys

```
