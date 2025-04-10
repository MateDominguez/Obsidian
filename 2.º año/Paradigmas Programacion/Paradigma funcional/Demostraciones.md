# Razonamiento ecuacional
Razonamos ecuacionalmente usando tres principios:
1. Principio de reemplazo
2. Principio de induccion estructural
3. Principio de extensionalidad funcional

Queremos demostrar que ciertas expresiones son equivalentes. 
¿Para que? 
* Para justificar que un algoritmo es correcto.
* Para posibilitar optimizaciones.

Asumimos que:
* Trabajamos con estructuras de datos finitas ([[Tipos Algebraicos|tipos de datos inductivos]]).
* Trabajamos con funciones totales.
	* Las ecuaciones deben cubrir todos los casos. 
	* La recursion siempre debe terminar.
* El programa no depende del orden de las ecuaciones.

---

## Principio de reemplazo
Sea `e1 = e2` una ecuacion del programa. Las siguientes operaciones preservan la igualdad de expresiones:
* Reemplazar cualquier instancia de e1 por e2.
* Reemplazar cualquier instancia de e2 por e1.

Si una igualdad se puede demostrar usando solo el principio de reemplazo, la igualdad vale **por definicion**.

El principio de reemplazo no sirve para todas las equivalencias.

---

# Induccion estructural
Cada tipo de datos tiene su propio principio de induccion.

En el caso general, tenemos un tipo de datos inductivo:
```
data T = CBase_1 <parametros>
		 ...3
		 CBase_n <parametros>
		 CRecursivo_1 <parametros>
		 ...
		 CRecursivo_m <parametros>
```

## Principio de induccion estructural
Sea $P$ una propiedad acerca de las expresiones tipo $T$ tal que: 
* $P$ vale sobre todos los constructores base de $T$. 
* $P$ vale sobre todos los constructores recursivos de $T$, asumiendo como hipotesis inductiva que vale para los parametros de tipo $T$.
 
 Entonces $\forall x::T.P(x)$.

Usando el principio de induccion estructural, se puede probar:
### Lema de generacion para pares
$$
\text{Si }p::(a,b),\text{ entonces }\exists x::a.\exists y::b.p=(x,y)
$$
### Lema de generacion para sumas
`data Either a b = Left a | Right b`
$$
\text{Si }e::Either~a~b,\text{entonces}
\begin{cases}
\text{o bien }\exists x::a.e=\text{Left }x \\
\text{o bien }\exists y::b.e=\text{Right }y
\end{cases}
$$

---

### Principio de induccion sobre booleanos
$$
\text{Si P(True) y P(False)} \to \forall x :: Bool. P(x)
$$
### Principio de induccion sobre pares
$$
\text{Si } \forall x::a.\forall y::b.P((x,y)) \text{ entonces } \forall p::(a,b).P(p)
$$

### Principio de induccion sobre naturales
`data Nat = Zero | Succ Nat`

$$
\begin{gather}
\text{Si }P(Zero) \text{ y } \forall n::Nat.(P(n)\to P(Succ~ n)), \text{ entonces } \forall n::Nat.P(n) \\
 \\
Donde: \\
\text{Hipotesis Inductiva}=P(n) \\
\text{Tesis Inductiva}=P(Succ~n)
\end{gather}
$$

---

### Intensional vs. extensional
Punto de vista **intensional**: 
Dos valores son iguales si estan construidos de la misma manera.

Punto de vista **extensional**: 
Dos valores son iguales si son indistinguibles al observarlos.

## Principio de extensionalidad funcional
Sean `f, g :: a -> b`
$\text{Si }(\forall x::a.f~x~=g~x)\text{ entonces }f=g$.

Para probar que dos funciones son iguales, basta probar que son iguales punto a punto.

---

## Pasos para demostrar una propiedad por induccion
1. Leer la propiedad, entenderla y convencerse de que es verdadera.
2. Plantear la propiedad como predicado unario.
3. Plantear el esquema de recursion.
4. Plantear y resolver el o los caso/s base.
5. Plantear y resolver el o los caso/s inductivo/s.
