# ## Chapter 4: Single-Qubit Gates

### 4.1 Quantum Gates as Unitary Operators

A quantum gate is a **unitary matrix** U satisfying:
```
U†U = UU† = I
```

where U† is the conjugate transpose and I is identity.

**Why unitary?**
- Preserves normalization: ||U|ψ⟩|| = ||ψ||
- Reversible: U^(-1) = U†
- Preserves inner products

**Example**: Check if H is unitary
```
H = (1/√2)[1   1]
           [1  -1]

H† = (1/√2)[1   1]  (H is Hermitian: H† = H)
            [1  -1]

H†H = (1/2)[1   1][1   1] = (1/2)[2  0] = [1  0] = I ✓
            [1  -1][1  -1]         [0  2]   [0  1]
```

### 4.2 Pauli Gates

**Pauli-X (NOT gate)**:
```
X = [0  1]
    [1  0]

Effect:
X|0⟩ = [0  1][1] = [0] = |1⟩
       [1  0][0]   [1]

X|1⟩ = [0  1][0] = [1] = |0⟩
       [1  0][1]   [0]

General: X(α|0⟩ + β|1⟩) = α|1⟩ + β|0⟩
```

**Example**:
```
|ψ⟩ = (1/√2)|0⟩ + (i/√2)|1⟩

X|ψ⟩ = (1/√2)|1⟩ + (i/√2)|0⟩
     = (i/√2)|0⟩ + (1/√2)|1⟩
```

**Pauli-Y**:
```
Y = [0  -i]
    [i   0]

Y|0⟩ = i|1⟩
Y|1⟩ = -i|0⟩

General: Y(α|0⟩ + β|1⟩) = iα|1⟩ - iβ|0⟩
```

**Example**:
```
|ψ⟩ = (3/5)|0⟩ + (4/5)|1⟩

Y|ψ⟩ = (3i/5)|1⟩ - (4i/5)|0⟩
     = -(4i/5)|0⟩ + (3i/5)|1⟩
```

**Pauli-Z (Phase flip)**:
```
Z = [1   0]
    [0  -1]

Z|0⟩ = |0⟩
Z|1⟩ = -|1⟩

General: Z(α|0⟩ + β|1⟩) = α|0⟩ - β|1⟩
```

**Example**:
```
|+⟩ = (1/√2)|0⟩ + (1/√2)|1⟩

Z|+⟩ = (1/√2)|0⟩ - (1/√2)|1⟩ = |-⟩
```

### 4.3 Hadamard Gate

```
H = (1/√2)[1   1]
           [1  -1]
```

**Action on basis states**:
```
H|0⟩ = (1/√2)(|0⟩ + |1⟩) = |+⟩
H|1⟩ = (1/√2)(|0⟩ - |1⟩) = |-⟩
```

**Key property**: Creates superposition
```
H[1] = (1/√2)[1   1][1] = (1/√2)[1] = |+⟩
  [0]          [1  -1][0]          [1]
```

**Example 1**: Starting from |0⟩
```
|ψ₀⟩ = |0⟩
|ψ₁⟩ = H|0⟩ = (1/√2)|0⟩ + (1/√2)|1⟩
```

**Example 2**: H is self-inverse (H² = I)
```
|ψ⟩ = |+⟩ = (1/√2)|0⟩ + (1/√2)|1⟩

H|ψ⟩ = H(1/√2)|0⟩ + H(1/√2)|1⟩
     = (1/√2)|+⟩ + (1/√2)|-⟩
     = (1/√2)[(1/√2)(|0⟩+|1⟩) + (1/√2)(|0⟩-|1⟩)]
     = (1/2)[2|0⟩]
     = |0⟩
```

**Example 3**: Creating interference
```
|ψ₀⟩ = |0⟩
|ψ₁⟩ = H|ψ₀⟩ = (1/√2)|0⟩ + (1/√2)|1⟩
|ψ₂⟩ = Z|ψ₁⟩ = (1/√2)|0⟩ - (1/√2)|1⟩
|ψ₃⟩ = H|ψ₂⟩ = |1⟩
```

### 4.4 Phase Gates

**S gate (Phase gate)**:
```
S = [1  0]
    [0  i]

S|0⟩ = |0⟩
S|1⟩ = i|1⟩
```

**Example**:
```
|+⟩ = (1/√2)|0⟩ + (1/√2)|1⟩

S|+⟩ = (1/√2)|0⟩ + (i/√2)|1⟩ = |+i⟩
```

**T gate (π/8 gate)**:
```
T = [1       0     ]
    [0  e^(iπ/4) ]

T|0⟩ = |0⟩
T|1⟩ = e^(iπ/4)|1⟩
```

**General phase gate**:
```
P(φ) = [1      0   ]
       [0  e^(iφ) ]

P(φ)|0⟩ = |0⟩
P(φ)|1⟩ = e^(iφ)|1⟩
```

**Example**: P(π) = Z
```
P(π) = [1      0   ] = [1   0] = Z
       [0  e^(iπ) ]   [0  -1]
```

**Relationship between gates**:
```
S = P(π/2) = T²
Z = S²
```

### 4.5 Rotation Gates

**Rotation around X-axis**:
```
Rx(θ) = [cos(θ/2)    -i·sin(θ/2)]
        [-i·sin(θ/2)  cos(θ/2)  ]
```

**Example**: Rx(π) = -iX
```
Rx(π) = [cos(π/2)   -i·sin(π/2)] = [0   -i] = -i[0  1] = -iX
        [-i·sin(π/2) cos(π/2)  ]   [-i   0]     [1  0]
```

**Rotation around Y-axis**:
```
Ry(θ) = [cos(θ/2)   -sin(θ/2)]
        [sin(θ/2)    cos(θ/2)]
```

**Example**: Ry(π/2) rotates |0⟩ to |+⟩
```
Ry(π/2)|0⟩ = [cos(π/4)  -sin(π/4)][1]
             [sin(π/4)   cos(π/4)][0]
           = [1/√2]  = (1/√2)|0⟩ + (1/√2)|1⟩ = |+⟩
             [1/√2]
```

**Rotation around Z-axis**:
```
Rz(θ) = [e^(-iθ/2)      0     ]
        [0          e^(iθ/2) ]
```

**Example**: Rz(π) introduces phase
```
Rz(π) = [e^(-iπ/2)     0    ] = [-i   0] = -iZ (up to global phase)
        [0         e^(iπ/2)]   [0    i]
```

### 4.6 Visualization: Circuit Diagrams

Single-qubit gate on a quantum circuit:
```
|ψ⟩ ──[G]── |ψ'⟩
```

**Example circuit**:
```
|0⟩ ──[H]──[S]──[H]──

Step by step:
|0⟩ → (1/√2)|0⟩ + (1/√2)|1⟩ → (1/√2)|0⟩ + (i/√2)|1⟩ → |1⟩
```

### 4.7 Complete Example: Building Arbitrary State

**Problem**: Create state |ψ⟩ = (3/5)|0⟩ + (4/5)|1⟩ starting from |0⟩

**Solution**: Use Ry rotation
```
We need: cos(θ/2) = 3/5
         sin(θ/2) = 4/5

θ/2 = arcsin(4/5) ≈ 53.13°
θ ≈ 106.26° ≈ 1.855 radians

Gate: Ry(1.855)
```

**Verify**:
```
Ry(1.855)|0⟩ = [cos(53.13°)][1]   [0.6]   [3/5]
               [sin(53.13°)][0] = [0.8] = [4/5]
```

---

[← Previous](./03_*.md) | [Next →](./05_*.md)