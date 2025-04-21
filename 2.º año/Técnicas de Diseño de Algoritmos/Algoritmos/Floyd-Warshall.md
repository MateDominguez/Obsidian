? Vertices no negativos, pero no ciclos con pesos negativos.

Complejidad temporal: $\Theta(V^3)$.

$$
D^{(k)} = 
\begin{cases}

\end{cases}
$$

```
Floyd-Warshall(W,n)
	D^(0) = W
	para k entre 1 y n
		sea D^(k) una matriz n*n
		para cada i entre 1 y n
			para cada k entre 1 y n
			 D^(k)[i,j] = min(D^(k-1)[i,j], D^(k-1)[i,l] + D^(k-1)[k,j])
return D^(n)
```