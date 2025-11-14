# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm

## AIM:
To design and implement a Python program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Start the program
2. Represent the city map as a weighted graph, where nodes represent blocks and edges represent travel times.
3. Take the current block of the EV as the source node
4. Store the locations of all charging stations
5. Use Dijkstra’s algorithm to compute the shortest distance from the source node to all other nodes in the graph.
6. Compare distances to find the nearest charging station with the minimum travel time
7. Display the shortest path and the total travel time
8.  If no charging station is reachable, display an appropriate message
9.   Stop the program

## Program:
```
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: SIVAKUMAR R
Register Number: 212223230209
*/

import java.util.*;

public class DijkstraEV {
    private static final int INF = Integer.MAX_VALUE;

    // Dijkstra's Algorithm
    public static int[] dijkstra(int[][] graph, int src) {
        int n = graph.length;
        int[] dist = new int[n];
        boolean[] visited = new boolean[n];

        Arrays.fill(dist, INF);
        dist[src] = 0;

        for (int count = 0; count < n - 1; count++) {
            int u = minDistance(dist, visited);
            visited[u] = true;

            for (int v = 0; v < n; v++) {
                if (!visited[v] && graph[u][v] != 0 && dist[u] != INF
                        && dist[u] + graph[u][v] < dist[v]) {
                    dist[v] = dist[u] + graph[u][v];
                }
            }
        }

        return dist;
    }

    // Find vertex with minimum distance
    private static int minDistance(int[] dist, boolean[] visited) {
        int min = INF, minIndex = -1;
        for (int v = 0; v < dist.length; v++) {
            if (!visited[v] && dist[v] <= min) {
                min = dist[v];
                minIndex = v;
            }
        }
        return minIndex;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Example graph represented as adjacency matrix
        int[][] graph = {
            {0, 4, 2, 0, 0},
            {4, 0, 5, 10, 0},
            {2, 5, 0, 3, 4},
            {0, 10, 3, 0, 1},
            {0, 0, 4, 1, 0}
        };

        // Node names for clarity
        String[] blocks = {"A", "B", "C", "D", "E"};

        System.out.print("Enter current block (A-E): ");
        char currentBlock = sc.next().charAt(0);

        int start = currentBlock - 'A';

        // Charging stations (for example D and E)
        int[] chargingStations = {3, 4}; // D, E

        int[] distances = dijkstra(graph, start);

        // Find nearest charging station
        int nearestStation = -1;
        int minDistance = INF;

        for (int station : chargingStations) {
            if (distances[station] < minDistance) {
                minDistance = distances[station];
                nearestStation = station;
            }
        }

        System.out.println("\n--- EV Charging Station Finder ---");
        if (nearestStation != -1) {
            System.out.println("Nearest charging station: Block " + blocks[nearestStation]);
            System.out.println("Shortest travel time: " + minDistance + " units");
        } else {
            System.out.println("No reachable charging station found.");
        }

        sc.close();
    }
}

```

## Output:

<img width="610" height="186" alt="image" src="https://github.com/user-attachments/assets/650ecbc8-4263-478e-a139-6dc5165c116f" />


## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
