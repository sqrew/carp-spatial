# Examples

## Efficient Ray-Grid Traversal

The `query-ray` function uses a 3D DDA algorithm to visit only the cells the ray actually passes through.

```carp
(use SpatialGrid)

(let [grid (new 10.0 10 10 10)
      ray (create-ray &(Vector3.init -5.0 5.0 5.0) &(Vector3.init 1.0 0.0 0.0))]
  (let [hits (query-ray-unique &grid &ray 100.0)]
    ;; 'hits' contains IDs of all objects in the ray's path
    ...))
```

## Neighborhood Queries

Useful for AI, physics, or particle effects where you need to find all objects near a specific point.

```carp
(let [grid (new 5.0 50 50 50)
      explosion-pos (Vector3.init 25.0 25.0 25.0)
      explosion-radius 10.0
      sphere (Sphere.init explosion-pos explosion-radius)]
  (let [victims (query-sphere-unique &grid &sphere)]
    (foreach [id victims]
      (apply-damage @id 100))))
```

## Management in a Game Loop

Standard pattern for a game engine: clear the grid every frame and re-insert active objects.

```carp
(defn update [grid entities]
  (do
    (clear! grid)
    (foreach [e entities]
      (insert! grid (get-aabb e) (get-id e)))))
```
