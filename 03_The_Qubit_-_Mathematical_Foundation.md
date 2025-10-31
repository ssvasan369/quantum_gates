# ## Chapter 3: The Qubit - Mathematical Foundation

### 3.1 Computational Basis

The standard basis for a qubit:
```
|0⟩ = [1]    |1⟩ = [0]
      [0]          [1]
```

These are **orthonormal**:
```
⟨0|0⟩ = 1,  ⟨1|1⟩ = 1
⟨0|1⟩ = 0,  ⟨1|0⟩ = 0
```

### 3.2 General Qubit State

Any qubit state:
```
|ψ⟩ = α|0⟩ + β|1⟩
```

where α, β ∈ ℂ (complex numbers)

**Normalization condition**: |α|² + |β|² = 1

**Matrix form**:
```
|ψ⟩ = α[1] + β[0] = [α]
       [0]     [1]   [β]
```

### 3.3 Example States

**Example 1**: Equal superposition
```
|+⟩ = (1/√2)|0⟩ + (1/√2)|1⟩ = [1/√2]
                                [1/√2]

Check: |1/√2|² + |1/√2|² = 1/2 + 1/2 = 1 ✓
```

**Example 2**: With phase
```
|ψ⟩ = (1/√2)|0⟩ + (i/√2)|1⟩ = [1/√2]
                               [i/√2]

Check: |1/√2|² + |i/√2|² = 1/2 + 1/2 = 1 ✓
```

**Example 3**: General with phase
```
|ψ⟩ = (3/5)|0⟩ + (4/5)e^(iπ/4)|1⟩

α = 3/5,  β = (4/5)e^(iπ/4)
|α|² + |β|² = 9/25 + 16/25 = 25/25 = 1 ✓
```

### 3.4 Bloch Sphere Representation

Any pure qubit state can be written as:
```
|ψ⟩ = cos(θ/2)|0⟩ + e^(iφ) sin(θ/2)|1⟩
```

where:
- θ ∈ [0, π]: polar angle
- φ ∈ [0, 2π): azimuthal angle

**Geometric interpretation**: Points on a unit sphere

**Special points**:
```
|0⟩: θ=0 (north pole)
|1⟩: θ=π (south pole)
|+⟩ = (|0⟩+|1⟩)/√2: θ=π/2, φ=0 (x-axis)
|-⟩ = (|0⟩-|1⟩)/√2: θ=π/2, φ=π (-x-axis)
|+i⟩ = (|0⟩+i|1⟩)/√2: θ=π/2, φ=π/2 (y-axis)
```

**Example**: Find θ and φ for |ψ⟩ = (1/√2)|0⟩ + (i/√2)|1⟩
```
cos(θ/2) = 1/√2  →  θ/2 = π/4  →  θ = π/2
e^(iφ) sin(θ/2) = i/√2
sin(θ/2) = 1/√2  ✓
e^(iφ) = i = e^(iπ/2)  →  φ = π/2
```

### 3.5 Properties of Quantum States

**Linearity**: If |ψ⟩ and |φ⟩ are states, then α|ψ⟩ + β|φ⟩ is a state (after normalization)

**Global phase irrelevance**: 
```
|ψ⟩ and e^(iθ)|ψ⟩ are physically equivalent
```

**Example**:
```
|ψ⟩ = (1/√2)|0⟩ + (1/√2)|1⟩
|φ⟩ = e^(iπ/3)[(1/√2)|0⟩ + (1/√2)|1⟩]

These represent the same physical state
```

**Relative phase matters**:
```
|ψ⟩ = (1/√2)|0⟩ + (1/√2)|1⟩
|φ⟩ = (1/√2)|0⟩ - (1/√2)|1⟩

These are different physical states!
```

---

[← Previous](./02_*.md) | [Next →](./04_*.md)