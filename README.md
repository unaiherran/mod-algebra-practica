# mod-algebra-practica
Se incluye en el repositorio tanto el notebook sin resolver como el resueltos (para consultar en el futuro). Tambien se incluye el directorio imagenes.

El archivo con la resolución es `ALG00.ipynb` tambien se incluyen el archivo `pruebas.ipnb`que simplemente tiene el ejercicio 6 con los prints  usados en el debug. Lo guardo por su valor documental

Practicamente todos los ejercicios contienen la explicación en el propio notebook, pero viendo que el ejercicio 6 requiere más comentarios  del que pueden incluirse en el el código para que se mantenga legible, lo explico aquí.

## Ejercicio 6

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
def nodosQueConectan (grafoOriginal, nodo): # Devuelve un conjunto con los nodos que conectan directamente con un nodo determinado
def quitarNodo (grafo, nodo):   #Devuelve un grafo basado en el grafo suminsitardo en el que se ha retirado un nodo
def camino(grafoOriginal, nodoA, nodoB):    #Devuelve True o False segun si hay un camino entre dos nodos
def buscaVertices(grafo, nodoInicial, listaDeNodos):    # devuelve una lista con todos los vertices que unen 'nodoInicial' con los nodos                                            # suministrados en 'listaDeNodos' de un 'grafo'
```

