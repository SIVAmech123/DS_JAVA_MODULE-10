# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE:11/11/25
## AIM:
To design and implement a Python program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm
1. Start the program
2. Represent the city junction map as a graph using an adjacency list (dictionary).
3. Define a function bfs(graph, start) that performs Breadth-First Search traversal:

Initialize a queue and a list to keep track of visited junctions.

Enqueue the starting junction.

While the queue is not empty:

Dequeue a junction and mark it as visited.

Print or store the junction in traversal order.
4.  In the main section:

Define the city map as a graph (each node represents a junction).

Take a starting junction as input (or use a fixed source).

Call the bfs() function to display reachable locations.
5.   Stop the program.

## Program:
```
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph.
Developed by: K Dilli babu 
RegisterNumber:  21222411015

*/

import java.util.*;

public class BFS_CityJunction {
    // Method to perform BFS traversal
    public static void bfs(Map<String, List<String>> graph, String start) {
        Set<String> visited = new HashSet<>();
        Queue<String> queue = new LinkedList<>();

        queue.add(start);
        visited.add(start);

        System.out.print("BFS Traversal starting from junction '" + start + "': ");

        while (!queue.isEmpty()) {
            String junction = queue.poll();
            System.out.print(junction + " ");

            // Visit all unvisited neighbors
            for (String neighbor : graph.get(junction)) {
                if (!visited.contains(neighbor)) {
                    visited.add(neighbor);
                    queue.add(neighbor);
                }
            }
        }
    }

    public static void main(String[] args) {
        // Representing the city junction map as a graph
        Map<String, List<String>> cityMap = new HashMap<>();
        cityMap.put("A", Arrays.asList("B", "C"));
        cityMap.put("B", Arrays.asList("A", "D", "E"));
        cityMap.put("C", Arrays.asList("A", "F"));
        cityMap.put("D", Arrays.asList("B"));
        cityMap.put("E", Arrays.asList("B", "F"));
        cityMap.put("F", Arrays.asList("C", "E"));

        System.out.println("City Junction Map: " + cityMap);

        // Starting junction
        String start = "A";

        // Perform BFS traversal
        bfs(cityMap, start);
    }
}

```

## Output:

<img width="738" height="121" alt="image" src="https://github.com/user-attachments/assets/0f286414-92a0-4a41-9b4d-a8b906b98ab6" />


## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
