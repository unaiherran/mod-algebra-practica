# mod-algebra-practica
Se incluye en el repositorio tanto el notebook sin resolver como el resueltos (para consultar en el futuro). Tambien se incluye el directorio imagenes.

El archivo con la resolución es `ALG00.ipynb` tambien se incluyen el archivo `pruebas.ipnb`que simplemente tiene el ejercicio 6 con los prints  usados en el debug. Lo guardo por su valor documental

### Ejercicio 1
La conjetura de Collatz dice:
Sea la siguiente operación, aplicable a cualquier número entero positivo:

Si el número es par, se divide entre 2.
Si el número es impar, se multiplica por 3 y se suma 1.

La conjetura dice que siempre alcanzaremos el 1 (y por tanto el ciclo 4, 2, 1) para cualquier número con el que comencemos. 

Se realiza una funcion en python que devuelve el mecanismo de la conjetura de Collatz

### Ejercicio 2

Se realiza un procedimiento que suma la clave al vector mensaje para encriptar. La funcion es reversible, y se utiliza el mismo metodo tanto para encriptar como para desencriptar.

### Ejercicio 3
Realizar este calculo de forma tradicional requiere multiplicar cada uno de los costes por la cantidad necesaria. Esto se puede realizar de una forma más directa mediante un producto escalar. Se implementa un procedimiento para realizar el producto escalar.

### Ejercicio 4
Para calcular cómo cobrariamos 13 € siendo cualquier resultado, tenemos que tener en cuenta que el pago que vamos a recibir es n veces lo apostado en el caballo ganador y que perderemos el dinero que hemos apostado a los otros caballos, lo que hace que planeemos este sistema de ecuaciones:

4x -  y  -  z = 13
-x + 3y  -  z = 13
-x -  y  + 2z = 13

Realizamos las verificaciones del sistema (si es compatible determinado, compatible indeterminado o incompatible) y resolvemos.

### Ejercicio 5



### Ejercicio 6

Para definir un grafo se usa la siguiente extructura:

`[({N1,N2},P1), ....,({NN-1,NN},PN)]`

Es decir, una lista de vertices, siendo cada vertice una tupla de un conjunto de nodos y un numero que indica el peso de ese vertice.

`(`
`{N1 , N2}` -> Conjunto de vertices
`,`
`P` -> Peso
`)`

Primero se definen las siguientes funciones:

```
def sumaPesos(grafo):       # Devuelve la suma de todos los pesos del grafo
def nodosEnGrafo(grafo):    # Devuelve un conjunto con los nodos que tiene el grafo
def pesoMaximo(grafo):      # devuelve el peso maximo en un grafo
def pesoMinimo(grafo):      # devuelve el peso maximo en un grafo.
def listaPesos(grafo, mayor=True):  #   Devuelve una lista ordenada de todos los pesos de un grafo
def nodosQueConectan (grafoOriginal, nodo): # Devuelve un conjunto con los nodos que conectan 
                                            # directamente con un nodo determinado
def quitarNodo (grafo, nodo):   # Devuelve un grafo basado en el grafo suminsitardo en el que se ha 
                                # retirado un nodo
def camino(grafoOriginal, nodoA, nodoB):    #Devuelve True o False segun si hay un camino entre dos nodos
def buscaVertices(grafo, nodoInicial, listaDeNodos):    # devuelve una lista con todos los vertices que unen
                                                        # 'nodoInicial' con los nodos suministrados en 
                                                        # 'listaDeNodos' de un 'grafo'
```

Con estas funciones implementamos el algoritmo **Grow**.
1) Empezamos con un grafo vacio
2) Añadimos el vertice con menor peso al grafo vacio
3) Vemos que nodos nos quedan por añadir
4) Añadimos el nodo que tenga un vertice que una con el arbol y tenga el valor más pequeño
5) Si siguen quedando nodos por añadir repetimos 4

Y el **Shrink**
1) Empezamos con el grafo completo
2) Buscamos el vertice con mas peso
3) Quitamos ese vertice
4) Miramos a ver si hemos dejado algun nodo sin conectar o si hemos generado dos islas (es decir que todos los nodos del grafo tienen que seguir conectados entre ellos
5) Si se da alguno de estos casos volvemos a añadir el vertice quitado
6) Iteramos con el siguinte vertice (hasta que no nos queden vertices)
