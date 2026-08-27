# carp-spatial

A high-performance static 3D spatial partitioning grid for the [Carp](https://github.com/carp-lang/Carp) programming language.

## Features

- **Static 3D Grid**: Optimized for fixed-volume simulation spaces.
- **Fast Queries**: Support for AABB, Sphere, and Ray-based spatial queries.
- **Raycasting (DDA)**: Efficiently walks the grid along a ray path to find relevant objects.
- **Zero-Allocation Insertion**: Designed for high-frequency updates in game loops.
- **Robustness**: Handles rays starting outside the grid and precision edge cases.


## Examples

See [examples.md](examples.md) for usage examples.
## Testing

Run the test suite with:

```bash
carp -x test/grid_test.carp
```

## License

MIT
