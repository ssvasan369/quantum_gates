## Chapter 11: Gate Decomposition

### 11.1 Euler Angle Decomposition

**Any single-qubit unitary**:
```
U(θ, φ, λ) = [cos(θ/2)           -e^(iλ)sin(θ/2)    ]
             [e^(iφ)sin(θ/2)   e^(i(φ+λ))cos(θ/2) ]
```

**Example 1**: Find angles for X gate
```
X = [0  1]
    [1  0]

Need: cos(θ/2) = 0 → θ = π
      e^(iφ)sin(π/2) = 1 → e^(iφ) = 1 → φ = 0
      -e^(iλ)sin(π/2) = 1 → e^(iλ) = -1 → λ = π

U(π, 0, π) = [0   -e^(iπ)]  = [0  1] = X ✓
             [1      0    ]    [1  0]
```

**Example 2**: Find angles for H gate
```
H = (1/√2)[1   1]
           [1  -1]

cos(θ/2) = 1/√2 → θ = π/2
e^(iφ)sin(π/4) = 1/√2 → e^(iφ) = 1 → φ = 0
-e^(iλ)sin(π/4) = 1/√2 → e^(iλ) = -1 → λ = π

U(π/2, 0, π) = (1/√2)[1   -e^(iπ)]  = (1/√2)[1   1] = H ✓
                      [1      0    ]          [1  -1]
```

### 11.2 ZYZ Decomposition

**Alternative form**:
```
U = e^(iα) Rz(β) Ry(γ) Rz(δ)
```

**Example**: Decompose X gate
```
X = [-i·Rz(π/2)]·Ry(π)·[Rz(π/2)]

Verify:
Rz(π/2) = [e^(-iπ/4)      0     ]  = [(1-i)/√2      0     ]
          [0         e^(iπ/4) ]    [0         (1+i)/√2]

Ry(π) = [cos(π/2)  -sin(π/2)]  = [0  -1]
        [sin(π/2)   cos(π/2)]    [1   0]

(Work through multiplication...)
Result: X (up to global phase) ✓
```

### 11.3 Controlled-U Decomposition

**Any controlled-U** can be built from:
- 2 CNOTs
- 3 single-qubit gates

**Form**:
```
CU = (I⊗A)·CNOT·(I⊗B)·CNOT·(I⊗C)

where ABC = I and e^(iα)AXBXC = U
```

**Example**: Build Controlled-Z from CNOT
```
CZ = (I⊗H)·CNOT·(I⊗H)

Verify on |11⟩:
|11⟩ → (I⊗H) → |1⟩⊗|−⟩ = (1/√2)(|10⟩ - |11⟩)
     → CNOT → (1/√2)(|11⟩ - |10⟩)  (flips when control=1)
     → (I⊗H) → (1/√2)[|1⟩⊗(|0⟩+|1⟩) - |1⟩⊗(|0⟩-|1⟩)]
               = (1/√2)[|1⟩⊗2|1⟩/√2]
               = -|11⟩

So CZ|11⟩ = -|11⟩ ✓
```

### 11.4 Gray Code for Multi-Controlled Gates

**Gray code**: Sequence where adjacent entries differ by 1 bit

**Use**: Efficiently implement multi-controlled gates

**Example**: 3-qubit Toffoli decomposition
```
Toffoli uses Gray code: 000, 001, 011, 010, 110, 111, 101, 100

Each step: one CNOT between adjacent codes
```

### 11.5 Complete Example: Building Arbitrary Two-Qubit Gate

**Problem**: Build general two-qubit unitary U

**Solution**: Canonical decomposition
```
U = (A₁⊗A₂)·e^(i(αXX + βYY + γZZ))·(B₁⊗B₂)

where Aᵢ, Bᵢ are single-qubit gates
```

**Steps**:
1. Find α, β, γ from U using eigenvalue decomposition
2. Find A₁, A₂, B₁, B₂ by solving equations
3. Implement e^(i(αXX + βYY + γZZ)) using CNOTs

**Concrete example**: Build SWAP

SWAP has structure:
```
SWAP = e^(iπ(XX + YY + ZZ)/4)

Using identity:
SWAP = CNOT₁₂ · CNOT₂₁ · CNOT₁₂
```

---