# Real-Time Food Delivery Dispatch and Route Optimization

A C program that models a 5-location delivery road network using a weighted undirected graph (stored as an adjacency matrix), simulates dynamic traffic delays using random weight updates, and computes the shortest route between a restaurant and a customer using **Dijkstra's Shortest Path Algorithm**.

---

## Features

* **Graph-Based Road Modeling:** Represents locations (`Location 0` to `Location 4`) as vertices and bidirectional roads as weighted edges in a `5 x 5` adjacency matrix.
* **Simulated Traffic Congestion:** Adds a random delay (`0` to `5`) to existing road weights before route calculation, keeping the undirected matrix symmetric.
* **Shortest-Path Routing (Dijkstra's Algorithm):** Computes the minimum-cost route from the selected restaurant location to the customer location and reconstructs the exact path using a `parent[]` array.
* **Input & Edge-Case Handling:** Validates non-numeric input, out-of-range location indices, same-source-and-destination selections, and unreachable destinations.

---

## Data Structures & Algorithms Used

* **Weighted Undirected Graph (`graph[V][V]`):** 2D adjacency matrix storing travel costs between locations (`0` indicates no direct road or self-loop; positive integers indicate road cost).
* **Helper Arrays in Dijkstra's Algorithm:**
  * `dist[]`: Stores the minimum known travel cost from the source location to each vertex.
  * `visited[]`: Tracks whether a vertex's shortest path has been finalized.
  * `parent[]`: Stores the predecessor vertex along the shortest path to reconstruct the route.
* **Traffic Perturbation (`addTraffic()`):** Uses `rand() % 6` after seeding with `srand((unsigned int)time(NULL))` to simulate unpredictable road delays.

---

## Complexity

* **Time Complexity:** $O(V^2)$ for Dijkstra's algorithm with an adjacency matrix of $V$ vertices (plus $O(V^2)$ to update edges during traffic simulation and $O(V)$ to reconstruct the path).
* **Space Complexity:** $O(V^2)$ for the adjacency matrix and $O(V)$ for the helper arrays.

---

## How to Compile and Run

### Using GCC (Linux / macOS / MinGW on Windows)

```bash
gcc dispatch_routing.c -o dispatch_routing -Wall -Wextra
./dispatch_routing
