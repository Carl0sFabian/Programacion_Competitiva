
# INFORME DEL TRABAJO FINAL - FUNDAMENTOS DE PROGRAMACIÓN COMPETITIVA (CC217)

**Carrera de Ciencias de la Computación**  
**Sección:** 271  

**Alumnos:**  
- Mendoza Quispe Carlos Fabian (U20231C416)  
- Moncada Olivares Elias David  
- Medina Oropeza Enzo Daniel  

**Julio 2025**

---

## 1. Introducción

El presente informe documenta el desarrollo del trabajo final del curso **Fundamentos de Programación Competitiva – CC217**, el cual tiene como propósito aplicar conocimientos algorítmicos y estructuras de datos en la resolución de problemas de alta complejidad mediante lenguajes de programación como C++. En un contexto académico, este tipo de entrenamiento fortalece la capacidad de los estudiantes para analizar, diseñar, implementar y evaluar soluciones computacionales eficientes, especialmente en escenarios competitivos o de resolución técnica de problemas reales.

El objetivo del trabajo es aplicar técnicas de programación como búsqueda en anchura (BFS), programación dinámica, y estructuras de datos avanzadas (como Trie y Fenwick Tree) para resolver problemas propuestos en plataformas reconocidas como HackerRank y LeetCode. Estas plataformas simulan entornos exigentes y representan estándares internacionales en competencias de codificación.

El método empleado consiste en seleccionar un conjunto representativo de ejercicios de dificultad creciente, analizar sus requerimientos computacionales, diseñar la solución lógica y programarla en lenguaje C++, verificando su correcta ejecución a través de pruebas proporcionadas por las plataformas.

Como conclusión preliminar, se destaca el fortalecimiento de habilidades clave como el pensamiento lógico, la eficiencia algorítmica y la claridad en el diseño e implementación de soluciones. Además, se logra una alineación directa con el *student outcome 2* de ABET, que requiere diseñar, implementar y evaluar soluciones computacionales en el contexto de sistemas de información.

---

## 2. Objetivo del estudiante

---
## 3. Plan de actividades

| Nombre completo                  | Tareas realizadas                                                                                  | Autoevaluación (%) |
|----------------------------------|------------------------------------------------------------------------------------------------------|----------------------|
| Carlos Fabian Mendoza Quispe    | Desarrallo de algoritmos (Programación Dinamica, Árbol Fenwick,Trie), validación de pruebas y  organización del repositorio          | 35%                    |
| Elias David Moncada Olivares    |                      |                     |
| Enzo Daniel Medina Oropeza      |                |                   |

## 4. Desarrollo

### Ejercicio 1
![Ejercicio 1](Exercises/Ejercicio_1.png)

El problema pertenece a la categoría de algoritmos de búsqueda y se resuelve eficientemente mediante el algoritmo de Búsqueda en Anchura (BFS). Esta técnica permite encontrar el número mínimo de pasos necesarios para ir de un punto de inicio a un punto final en un grafo no ponderado, siendo ideal cuando se busca la menor cantidad de movimientos entre nodos.

Este desafío se encuentra en la plataforma de programación competitiva HackerRank, la cual permite resolver problemas prácticos de estructuras de datos, algoritmos, matemáticas, inteligencia artificial, entre otros. En este caso, el problema forma parte de la sección de grafos.

El enlace directo al enunciado del problema en HackerRank es el siguiente:

https://www.hackerrank.com/challenges/the-quickest-way-up/problem

El problema plantea una simulación del clásico juego de mesa “Serpientes y Escaleras”. El jugador comienza en la casilla 1 y debe llegar a la casilla 100 lanzando un dado, cuyo resultado puede ser cualquier número del 1 al 6. Si cae en una casilla donde hay una escalera, sube automáticamente hasta el extremo superior de esta; si cae en una serpiente, desciende hasta el extremo inferior. El objetivo es encontrar la mínima cantidad de lanzamientos de dado necesarios para alcanzar la casilla 100, considerando todas las escaleras y serpientes presentes en el tablero. Pueden existir múltiples escenarios (casos de prueba), cada uno con diferentes configuraciones de escaleras y serpientes.

La solución implementada en lenguaje C + + utiliza un vector para simular el tablero y una cola para realizar la búsqueda en anchura. Cada casilla del tablero es tratada como un nodo y cada posible lanzamiento del dado (de 1 a 6) es una arista hacia otro nodo. Se marcan las casillas ya visitadas para evitar ciclos, y se simula el avance del jugador tomando en cuenta los cambios de posición provocados por escaleras o serpientes.

A continuación, se presenta el código completo del algoritmo desarrollado en C++:

## 📊 C++ Snakes and Ladders Solver

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

int quickestWayUp(const vector<pair<int, int>>& ladders, const vector<pair<int, int>>& snakes) {
    vector<int> board(101);
    for (int i = 1; i <= 100; ++i)
        board[i] = i;

    for (const auto& ladder : ladders)
        board[ladder.first] = ladder.second;

    for (const auto& snake : snakes)
        board[snake.first] = snake.second;

    vector<bool> visited(101, false);
    queue<pair<int, int>> q;
    q.push({1, 0});
    visited[1] = true;

    while (!q.empty()) {
        int pos = q.front().first;
        int moves = q.front().second;
        q.pop();

        if (pos == 100)
            return moves;

        for (int dice = 1; dice <= 6; ++dice) {
            int next = pos + dice;
            if (next <= 100 && !visited[board[next]]) {
                visited[board[next]] = true;
                q.push({board[next], moves + 1});
            }
        }
    }

    return -1;
}

int main() {
    int t;
    cin >> t;
    vector<int> resultados;

    while (t--) {
        int n;
        cin >> n;
        vector<pair<int, int>> ladders(n);
        for (int i = 0; i < n; ++i)
            cin >> ladders[i].first >> ladders[i].second;

        int m;
        cin >> m;
        vector<pair<int, int>> snakes(m);
        for (int i = 0; i < m; ++i)
            cin >> snakes[i].first >> snakes[i].second;

        resultados.push_back(quickestWayUp(ladders, snakes));
    }

    for (int res : resultados)
        cout << res << endl;

    return 0;
}
```

### Ejercicio 2
![Ejercicio 2](Exercises/Ejercicio_2.png)

### Ejercicio 3
![Ejercicio 3](Exercises/Ejercicio_3.png)

### Ejercicio 4
![Ejercicio 4](Exercises/Ejercicio_4.png)

