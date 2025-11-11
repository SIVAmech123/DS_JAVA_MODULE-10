# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE:11/11/25
## AIM:
To design and implement a Python program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm
1. Start the program.
2. Represent the heritage town map as a graph using a HashMap where each key is an attraction and its value is a list of connected attractions (walking paths).
Count the total number of reachable attractions.
3. Implement a BFS traversal to:

Visit all reachable attractions from a given starting attraction.

Count the total number of reachable attractions.

4.  Implement another BFS-based shortest path algorithm that:

Uses a queue and a distance map.

Tracks the shortest number of hops (edges) from the start to the target attraction.
5.   In the main() method:

Define the map (graph).

Take a starting and target attraction.

Display the reachable attractions and shortest distance.

Stop the program.

## Program:
```
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: Dilli babu K
RegisterNumber:  212224110015
*/

import java.util.*;

public class HeritageTownBFS {

    // Method to perform BFS traversal and return reachable attractions
    public static Set<String> bfsReachable(Map<String, List<String>> graph, String start) {
        Set<String> visited = new HashSet<>();
        Queue<String> queue = new LinkedList<>();

        queue.add(start);
        visited.add(start);

        while (!queue.isEmpty()) {
            String attraction = queue.poll();
            for (String neighbor : graph.get(attraction)) {
                if (!visited.contains(neighbor)) {
                    visited.add(neighbor);
                    queue.add(neighbor);
                }
            }
        }
        return visited;
    }

    // Method to find the shortest number of paths (minimum hops) using BFS
    public static int shortestPath(Map<String, List<String>> graph, String start, String target) {
        Queue<String> queue = new LinkedList<>();
        Map<String, Integer> distance = new HashMap<>();

        queue.add(start);
        distance.put(start, 0);

        while (!queue.isEmpty()) {
            String current = queue.poll();

            // If we reach the target, return the distance
            if (current.equals(target)) {
                return distance.get(current);
            }

            for (String neighbor : graph.get(current)) {
                if (!distance.containsKey(neighbor)) {
                    distance.put(neighbor, distance.get(current) + 1);
                    queue.add(neighbor);
                }
            }
        }

        // Return -1 if target is unreachable
        return -1;
    }

    public static void main(String[] args) {
        // Representing the heritage town map as a graph
        Map<String, List<String>> townMap = new HashMap<>();
        townMap.put("Museum", Arrays.asList("Temple", "Fort"));
        townMap.put("Temple", Arrays.asList("Museum", "Market", "Park"));
        townMap.put("Fort", Arrays.asList("Museum", "River"));
        townMap.put("Market", Arrays.asList("Temple", "Library"));
        townMap.put("Library", Arrays.asList("Market"));
        townMap.put("River", Arrays.asList("Fort", "Park"));
        townMap.put("Park", Arrays.asList("Temple", "River"));

        System.out.println("Heritage Town Map: " + townMap);

        String start = "Museum";
        String target = "Library";

        // Find all reachable attractions
        Set<String> reachable = bfsReachable(townMap, start);
        System.out.println("\nReachable attractions from '" + start + "': " + reachable);
        System.out.println("Total reachable attractions: " + reachable.size());

        // Find shortest path (minimum hops)
        int distance = shortestPath(townMap, start, target);
        if (distance != -1)
            System.out.println("\nShortest path from '" + start + "' to '" + target + "' = " + distance + " hops.");
        else
            System.out.println("\nNo path exists from '" + start + "' to '" + target + "'.");
    }
}

```

## Output:

<img width="1631" height="302" alt="image" src="https://github.com/user-attachments/assets/55fcf9bd-db87-4183-9d53-1562a2e10c9b" />


## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
