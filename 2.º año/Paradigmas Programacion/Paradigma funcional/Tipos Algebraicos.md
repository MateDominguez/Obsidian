Se definien con la clausula `data`.
```
data T = CBase_1 <parametros>
			...
			CBase_n <parametros>
			CRecursivo_1 <parametros>
			...
			CRecursivo_m <parametros>
```
* Los constructores pueden tomar parametros.
* Los constructores base no reciben parametros de tipo `T`.
* Los valores del tipo `T` son los que se pueden construir aplicando constructores base y recursivos un numero finito de veces.

Algunos constructores pueden ser recursivos, si lo hay, debe haber por lo menos un constructor no recursivo.

Las funciones sobre tipos de datos con constructores recursivos normalmente se definen por recursion.