# Overview
This project applies Evolutionary Algorithms (EAs) to solve the Traveling Salesman Problem (TSP).  
The TSP is a classic NP-hard optimization problem where the goal is to find the shortest possible tour that visits each city exactly once and returns to the starting point.

Each city in the TSP instance is represented by its index in a distance matrix, provided by the files in the `/problems` folder.  
A solution (individual) is encoded as a vector of city indices indicating the visiting order.  
The fitness (cost) of a solution is the total distance of the corresponding tour, which must be **minimized**.

## Algorithm Components

- Representation: A permutation of city indices (e.g., `[0, 1, 2, 3, …]`)
- Fitness Function (`cost`): Sum of distances along the tour (including return to start)
- Initialization: Population initialized with random permutations
- Parent Selection*: `tournament_selection` and `roulette_wheel_selection` (tested comparatively)
- Crossover Operator: *Order Crossover (OX)*
- Mutation Operator: *Swap Mutation* as a starting point; later, other methods tested (*Inversion*, *Insert*)
Operators were chosen based on standard TSP EA practice, and the mutation rate was set adaptively, depending on the rate `current_generation/total_generations`
- Replacement Strategy: only (μ + λ) was considered
- Termination:  Fixed number of generations proportional to problem size, i.e., `NUM_GENERATIONS=NUM_CITIES×150`

## Procedure
All analyses (selection comparison, operator testing, output analysis) were conducted on the small-scale 10-city problem for interpretability and efficiency.
The best-performing configuration was later applied to larger instances (20, 50 and 100 cities).
Each configuration was tested across multiple seeds. Metrics recorded included:
- Best distance per generation
- Final best distance
- Success rate (within 5% of best overall)
- Total runtime per problem 
PLEASE NOTE: due to time constraints, results were finalized up to size 100; problems with higher number of cities are not solved in this notebook.


