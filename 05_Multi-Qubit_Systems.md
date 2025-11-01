## Chapter 5: Multi-Qubit Systems

### 5.1 Two-Qubit Systems

**Computational basis** (4 states):
```
|00⟩ = [1]    |01⟩ = [0]    |10⟩ = [0]    |11⟩ = [0]
       [0]           [1]           [0]           [0]
       [0]           [0]           [1]           [0]
       [0]           [0]           [0]           [1]
```

**General state**:
```
|ψ⟩ = α₀₀|00⟩ + α₀₁|01⟩ + α₁₀|10⟩ + α₁₁|11⟩

where |α₀₀|² + |α₀₁|² + |α₁₀|² + |α₁₁|² = 1
```

**Matrix form**:
```
|ψ⟩ = [α₀₀]
      [α₀₁]
      [α₁₀]
      [α₁₁]
```

### 5.2 Tensor Product (⊗)

To combine separate qubits, we use the tensor product.

**Definition**: For vectors
```
|ψ⟩ = [a]    |φ⟩ = [c]
      [b]          [d]

|ψ⟩ ⊗ |φ⟩ = [a] ⊗ [c] = [ac]
            [b]   [d]   [ad]
                        [bc]
                        [bd]
```

**Example 1**: |0⟩ ⊗ |0⟩ = |00⟩
```
|0⟩ ⊗ |0⟩ = [1] ⊗ [1] = [1·1]   [1]
            [0]   [0]   [1·0] = [0] = |00⟩
                        [0·1]   [0]
                        [0·0]   [0]
```

**Example 2**: |0⟩ ⊗ |1⟩ = |01⟩
```
|0⟩ ⊗ |1⟩ = [1] ⊗ [0] = [1·0]   [0]
            [0]   [1]   [1·1] = [1] = |01⟩
                        [0·0]   [0]
                        [0·1]   [0]
```

**Example 3**: |+⟩ ⊗ |0⟩
```
|+⟩ ⊗ |0⟩ = [(1/√2)] ⊗ [1]
            [(1/√2)]   [0]

= [(1/√2)·1]   [1/√2]
  [(1/√2)·0] = [  0 ]
  [(1/√2)·1]   [1/√2]
  [(1/√2)·0]   [  0 ]

= (1/√2)|00⟩ + (1/√2)|10⟩
```

**Example 4**: General superposition
```
|ψ⟩ = (α|0⟩ + β|1⟩) ⊗ (γ|0⟩ + δ|1⟩)

Expanding:
= αγ|00⟩ + αδ|01⟩ + βγ|10⟩ + βδ|11⟩
```

**Concrete example**:
```
|ψ⟩ = [(1/√2)|0⟩ + (1/√2)|1⟩] ⊗ [(1/√2)|0⟩ + (1/√2)|1⟩]

= (1/2)|00⟩ + (1/2)|01⟩ + (1/2)|10⟩ + (1/2)|11⟩
```

### 5.3 Tensor Product of Matrices

For gates, tensor product works similarly:

**Definition**:
```
A ⊗ B = [a₁₁B  a₁₂B]
        [a₂₁B  a₂₂B]
```

**Example**: X ⊗ I
```
X ⊗ I = [0  1] ⊗ [1  0]
        [1  0]   [0  1]

= [0·[1  0]  1·[1  0]]   [0  0  1  0]
  [  [0  1]    [0  1]]   [0  0  0  1]
  [1·[1  0]  0·[1  0]] = [1  0  0  0]
  [  [0  1]    [0  1]]   [0  1  0  0]
```

This gate applies X to first qubit, leaves second unchanged.

**Example**: I ⊗ X
```
I ⊗ X = [1  0] ⊗ [0  1]
        [0  1]   [1  0]

= [1·[0  1]  0·[0  1]]   [0  1  0  0]
  [  [1  0]    [1  0]]   [1  0  0  0]
  [0·[0  1]  1·[0  1]] = [0  0  0  1]
  [  [1  0]    [1  0]]   [0  0  1  0]
```

This gate applies X to second qubit, leaves first unchanged.

### 5.4 Multi-Qubit Gate Application

**Gate on specific qubit**:
- First qubit: U ⊗ I ⊗ I ⊗ ...
- Second qubit: I ⊗ U ⊗ I ⊗ ...
- Third qubit: I ⊗ I ⊗ U ⊗ ...

**Example**: Apply H to first qubit of |00⟩
```
(H ⊗ I)|00⟩ = (H|0⟩) ⊗ (I|0⟩)
            = |+⟩ ⊗ |0⟩
            = (1/√2)(|0⟩ + |1⟩) ⊗ |0⟩
            = (1/√2)(|00⟩ + |10⟩)
```

**Example**: Apply H to both qubits of |00⟩
```
(H ⊗ H)|00⟩ = (H|0⟩) ⊗ (H|0⟩)
            = |+⟩ ⊗ |+⟩
            = [(1/√2)(|0⟩+|1⟩)] ⊗ [(1/√2)(|0⟩+|1⟩)]
            = (1/2)(|00⟩ + |01⟩ + |10⟩ + |11⟩)
```

### 5.5 Separable vs Entangled States

**Separable state**: Can be written as |ψ⟩ = |ψ₁⟩ ⊗ |ψ₂⟩

**Example**:
```
|ψ⟩ = (1/2)|00⟩ + (1/2)|01⟩ + (1/2)|10⟩ + (1/2)|11⟩
    = |+⟩ ⊗ |+⟩  (separable)
```

**Entangled state**: Cannot be written as a tensor product

**Example**:
```
|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)  (entangled)
```

**Test for entanglement**: Try to factor
```
|ψ⟩ = α₀₀|00⟩ + α₀₁|01⟩ + α₁₀|10⟩ + α₁₁|11⟩

Separable if: α₀₀·α₁₁ = α₀₁·α₁₀

For |Φ⁺⟩: α₀₀=1/√2, α₀₁=0, α₁₀=0, α₁₁=1/√2
(1/√2)·(1/√2) = 1/2 ≠ 0 = 0·0
Not separable! → Entangled
```

### 5.6 Three-Qubit Systems

**Basis states**: 8 states |000⟩, |001⟩, ..., |111⟩

**Example state**:
```
|ψ⟩ = Σ αᵢⱼₖ |ijk⟩  where i,j,k ∈ {0,1}

General form (8 dimensions):
|ψ⟩ = [α₀₀₀]
      [α₀₀₁]
      [α₀₁₀]
      [α₀₁₁]
      [α₁₀₀]
      [α₁₀₁]
      [α₁₁₀]
      [α₁₁₁]
```

**Example**: GHZ state
```
|GHZ⟩ = (1/√2)(|000⟩ + |111⟩)

= [1/√2]
  [  0 ]
  [  0 ]
  [  0 ]
  [  0 ]
  [  0 ]
  [  0 ]
  [1/√2]
```

---