## Definición
Una álgebra booleana es una 6-tupla $(X, \vee, \wedge, \neg, 0, 1)$ que consiste en un conjunto $X$ provisto de:

- Dos operaciones binarias:
    - $\vee$ (también denotada por $+$, generalmente llamada "o")
    - $\wedge$ (también denotada por $\times$ o por $\cdot$, generalmente llamada "y")
- Una operación unaria:
    - $\neg$ (también denotada por $\sim$ o por una barra superior, generalmente llamada "no")
- Dos constantes:
    - $0$ (también denotada por $\bot$ o por $F$, generalmente llamada "cero" o "falso")
    - $1$ (también denotada por $\top$ o por $V$, generalmente llamada "uno" o "verdadero")

Y satisfaciendo los siguientes axiomas, para cualesquiera $a, b, c \in X$:
### Propiedades

| Propiedad               | OR                                                   | AND                                                    |
| ----------------------- | ---------------------------------------------------- | ------------------------------------------------------ |
| Asociativa              | $(a \vee b) \vee c = a \vee (b \vee c)$              | $(a \wedge b) \wedge c = a \wedge (b \wedge c)$        |
| Conmutativa             | $a \vee b = b \vee a$                                | $a \wedge b = b \wedge a$                              |
| Absorbente              | $a \wedge (a \vee b) = a$                            | $a \vee (a \wedge b) = a$                              |
| Distributiva            | $a \vee (b \wedge c) = (a \vee b) \wedge (a \vee c)$ | $a \wedge (b \vee c) = (a \wedge b) \vee (a \wedge c)$ |
| Elemento Neutro         | $a \vee 0 = a$                                       | $a \wedge 1 = a$                                       |
| Elemento Complementario | $a \vee \neg a = 1$                                  | $a \wedge \neg a = 0$                                  |
