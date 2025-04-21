---
aliases: []
---
# Programacion dinamica
Esta tecnica es aplicada tıpicamente a problemas de **optimizacion combinatoria**, donde puede haber muchas soluciones factibles, cada una con un valor (o costo) asociado y prentendemos obtener la solucion con mejor valor (o menor costo). Tambien resulta adecuada para algunos problemas de naturaleza recursiva.

Al igual que [[Divide & Conquer|D&C]], divide al problema en subproblemas de tamanos menores, que son mas faciles de resolver. Una vez resueltos estos subproblemas, se combinan las soluciones obtenidas para generar la solucion del problema original. 

## Memoizacion
Evita resolver mas de una vez un mismo subproblema en diferentes llamadas recursivas. Para esto mantiene una estructura de datos donde almacena los resultados que ya han sido calculados hasta el momento para su posterior reutilizacion si se repite una llamada a un subproblema. Entonces, cuando se hace una llamada recursiva a un subproblema primero se chequea si este subproblema ya ha sido resuelto. Si lo fue, se utiliza el resultado almacenado. En caso contrario, se realiza la llamada recursiva.
Si estamos seguros que un subproblema no sera llamado nuevamente, no es necesario que almacenemos la solucion a este subproblema, ahorrando asi espacio.

Si bien las soluciones de programacion dinamica son pensada como funciones recursivas top-down, algunas veces una implementacion no resursiva bottom-up puede llegar a resolutar en algoritmos con mejor tiempo de ejecucion.

**Como construir una solucion de programacion dinamica:**
1. Definir los subproblemas.
2. Relacionarlos y generar la transicion.
3. Armar el Directed Acyclic Graph (DAG) de estados. Chekear que no haya ciclos.
4. Defino los casos base.
5. Agrupacion de resultados para el problema original.
6. Analizar complejidad.