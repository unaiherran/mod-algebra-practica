# mod-algebra-practica
Se incluye en el repositorio tanto el notebook sin resolver como el resueltos (para consultar en el futuro). Tambien se incluye el directorio imagenes.

El archivo con la resolución es `ALG00.ipynb` tambien se incluyen el archivo `pruebas.ipnb`que simplemente tiene el ejercicio 6 con los prints  usados en el debug. Lo guardo por su valor documental

Practicamente todos los ejercicios contienen la explicación en el propio notebook, pero viendo que el ejercicio 6 requiere más comentarios  del que pueden incluirse en el el código para que se mantenga legible, lo explico aquí.

Para definir un grafo se usa la siguiente extructura:

`[({N1,N2},P1), ....,({NN-1,NN},PN)]`

Es decir, una lista de vertices, siendo cada vertice una tupla de un conjunto de nodos y un numero que indica el peso de ese vertice.

`(`
`{N1 , N2}` -> Conjunto de vertices
`,`
`P` -> Peso
`)`

Primero se definen las siguientes 
def sumaPesos(grafo):
    suma = 0
    for i in grafo:
        suma = suma + i[1]
    return suma

def nodosEnGrafo(grafo):
    # Esta funcion devuelve un conjunto con todos los nodos existentes en un grafo
    nodos = set()
    for i in grafo:
        for e in i[0]:
            nodos.add(e)    
    return nodos

def pesoMaximo(grafo):
    # devuelve el peso maximo en un grafo
    peso = 0
    for v in grafo:
        if peso<v[1]:
            peso = v[1]
    return peso

def pesoMinimo(grafo):
    if len(grafo) == 0:
        return 0
    else:
        peso = sumaPesos(grafo)
        for v in grafo:
            if peso > v[1]:
                peso = v[1]
        return peso
    
def listaPesos(grafo, mayor=True):
    l = []
    for i in grafo:
        l.append(i[1])
    l.sort(reverse=mayor)
    return l

def nodosQueConectan (grafoOriginal, nodo):
    nodos = set()
    
    for v in grafoOriginal:
        if nodo in v[0]:
            nodos = nodos | (v[0])
    nodos = nodos - {nodo}
    return nodos

def quitarNodo (grafo, nodo):
    grafoCopia = grafo.copy()
    for v in grafo:
        if nodo in v[0]:
            grafoCopia.remove(v)
    return grafoCopia


def camino(grafoOriginal, nodoA, nodoB):
    grafo = grafoOriginal.copy()
    # print("Probando camino entre ", nodoA, nodoB)
    
    #vemos si hay un camino directo
    directo = False
    for v in grafo:
        # print(v[0])
        if (nodoA in v[0]) and (nodoB in v[0]):
            # print(nodoA,nodoB, "Directo")
            return True
    
    nodosParaBuscar = nodosQueConectan(grafo, nodoA)
    # quitar los vertices que unen nodoA con nodosParaBuscar
    nuevoGrafo = quitarNodo(grafo, nodoA)
    
    for e in nodosParaBuscar:
        if camino(nuevoGrafo,e,nodoB): return True

def buscaVertices(grafo, nodoInicial, listaDeNodos):
    # devuelve una lista con todos los vertices que unen 'nodoInicial' con los nodos suministrados en 
    # 'listaDeNodos' de un 'grafo'
    l = []
    for i in grafo:
        nodos = i[0].copy()
        unNodo = nodos.pop()
        otroNodo = nodos.pop()
        if (unNodo == nodoInicial and otroNodo in listaDeNodos) or (otroNodo 
                                                                    == nodoInicial and unNodo in listaDeNodos):
            l.append(i)
    return l
