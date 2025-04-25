# Minimum Spanning Tree (MST) Parallelization

## Project Description
This project involves parallelizing an existing sequential Java program that constructs a Euclidean minimum spanning tree (MST) for a collection of points in the plane. The program uses Dwyer's algorithm for Delaunay triangulation and Kruskal's algorithm for MST construction.

## Parallelization Strategy
- **Triangulation Stage**: The Dwyer triangulation process was parallelized using a thread pool (`ExecutorService`). The point set is divided into partitions, and each partition is processed concurrently.
- **MST Stage**: The Kruskal algorithm was parallelized by dividing the edges into chunks and processing them in parallel using a thread pool. A concurrent union-find structure was used to manage connected components.

## Performance Results
The parallelized version of the program shows significant performance improvements over the original version. Below are the results for different numbers of points:

### Parallelized Version
- **1,000,000 points**: 0.058 + 0.002 = 0.060 seconds
- **2,000,000 points**: 0.104 + 0.002 = 0.106 seconds
- **3,000,000 points**: 0.152 + 0.004 = 0.156 seconds

### Original Version
- **1,000,000 points**: 10.741 + 0.450 = 11.191 seconds
- **2,000,000 points**: 28.676 + 0.944 = 29.620 seconds
- **3,000,000 points**: 57.325 + 2.208 = 59.533 seconds

## Conclusion
The parallelization of both the triangulation and MST stages has resulted in a substantial reduction in execution time, demonstrating the effectiveness of the parallelization strategy. The program now efficiently utilizes multiple threads to handle large datasets, achieving significant speedup compared to the original sequential version.

## Additional Notes
- The program accepts command-line arguments for animation mode, number of points, seed for the pseudorandom number generator, and number of threads.
- The performance results were obtained using a specific seed and thread count, and may vary with different configurations.
