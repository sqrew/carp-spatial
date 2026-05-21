# carp-spatial

A high-performance static 3D spatial partitioning grid for the [Carp](https://github.com/carp-lang/Carp) programming language.

## Features

- **Static 3D Grid**: Optimized for fixed-volume simulation spaces.
- **Fast Queries**: Support for AABB, Sphere, and Ray-based spatial queries.
- **Raycasting (DDA)**: Efficiently walks the grid along a ray path to find relevant objects.
- **Zero-Allocation Insertion**: Designed for high-frequency updates in game loops.
- **Robustness**: Handles rays starting outside the grid and precision edge cases.

## Usage

```carp
(load "carp-spatial/grid.carp")
(use SpatialGrid)

(defn main []
  ;; Create a 10x10x10 grid with 100.0 unit cells
  (let [grid (new 100.0 10 10 10)
        box (AABB.init (Vector3.init 50.0 50.0 50.0) (Vector3.init 150.0 150.0 150.0))]
    (do
      ;; Insert object ID 42
      (insert! &grid &box 42)
      
      ;; Query by AABB
      (let [results (query-unique &grid &box)]
        (IO.println &(str &results)))
        
      ;; Query by Ray
      (let [ray (create-ray &(Vector3.init 0.0 0.0 0.0) &(Vector3.init 1.0 1.0 1.0))
            ray-results (query-ray-unique &grid &ray 1000.0)]
        (IO.println &(str &ray-results))))))
```

## Testing

Run the test suite with:

```bash
carp -x test/grid_test.carp
```

## License

MIT
