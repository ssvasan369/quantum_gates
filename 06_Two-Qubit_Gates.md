# ## Chapter 6: Two-Qubit Gates

### 6.1 CNOT (Controlled-NOT) Gate

The CNOT gate is the most important two-qubit gate.

**Structure**: 
- First qubit: **control**
- Second qubit: **target**

**Action**: Flip target if control is |1⟩
```
CNOT|00⟩ = |00⟩  (control=0, target unchanged)
CNOT|01⟩ = |01⟩  (control=0, target unchanged)
CNOT|10⟩ = |11⟩  (control=1, target flipped)
CNOT|11⟩ = |10⟩  (control=1, target flipped)
```

**Matrix form**:
```
CNOT = [1  0  0  0]
       [0  1  0  0]
       [0  0  0  1]
       [0  0  1  0]
```

**Example 1**: Creating entanglement
```
Step 1: |00⟩
Step 2: (H⊗I)|00⟩ = (1/√2)(|00⟩ + |10⟩)
Step 3: CNOT[(1/√2)(|00⟩ + |10⟩)]
      = (1/√2)(CNOT|00⟩ + CNOT|10⟩)
      = (1/√2)(|00⟩ + |11⟩) = |Φ⁺⟩  (Bell state!)
```

**Example 2**: With superposition
```
|ψ⟩ = (α|0⟩ + β|1⟩) ⊗ |0⟩ = α|00⟩ + β|10⟩

CNOT|ψ⟩ = α·CNOT|00⟩ + β·CNOT|10⟩
        = α|00⟩ + β|11⟩
```

**Circuit diagram**:
```
q₀: ──●──   (control)
      │
q₁: ──⊕──   (target)
```

**Example 3**: Testing separability
```
Initial: |ψ⟩ = (1/√2)|0⟩ ⊗ |0⟩ = (1/√2)|00⟩  (separable)

After H⊗I: (1/2)(|00⟩ + |10⟩)  (separable)

After CNOT: (1/2)(|00⟩ + |11⟩)  (entangled!)
```

### 6.2 Controlled-U Gates

**General controlled gate**: Apply U to target if control is |1⟩

**Matrix form**:
```
CU = [I  0]  = [1  0  0  0]
     [0  U]    [0  1  0  0]
               [0  0  u₁₁ u₁₂]
               [0  0  u₂₁ u₂₂]
```

**Controlled-Z (CZ)**:
```
CZ = [1  0  0   0]
     [0  1  0   0]
     [0  0  1   0]
     [0  0  0  -1]

Action:
CZ|00⟩ = |00⟩
CZ|01⟩ = |01⟩
CZ|10⟩ = |10⟩
CZ|11⟩ = -|11⟩  (adds phase)
```

**Example**: CZ on superposition
```
|ψ⟩ = (1/2)(|00⟩ + |01⟩ + |10⟩ + |11⟩)

CZ|ψ⟩ = (1/2)(|00⟩ + |01⟩ + |10⟩ - |11⟩)
```

**Controlled-Phase**:
```
CP(φ) = [1  0  0       0   ]
        [0  1  0       0   ]
        [0  0  1       0   ]
        [0  0  0  e^(iφ)  ]
```

### 6.3 SWAP Gate

**Action**: Exchange two qubits
```
SWAP|00⟩ = |00⟩
SWAP|01⟩ = |10⟩
SWAP|10⟩ = |01⟩
SWAP|11⟩ = |11⟩
```

**Matrix**:
```
SWAP = [1  0  0  0]
       [0  0  1  0]
       [0  1  0  0]
       [0  0  0  1]
```

**Example**:
```
|ψ⟩ = α|01⟩ + β|10⟩

SWAP|ψ⟩ = α·SWAP|01⟩ + β·SWAP|10⟩
        = α|10⟩ + β|01⟩
```

**Decomposition**: SWAP can be built from 3 CNOTs
```
SWAP = CNOT₁₂ · CNOT₂₁ · CNOT₁₂
```

### 6.4 Bell States (Maximally Entangled)

The four Bell states form an orthonormal basis:

```
|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)
|Φ⁻⟩ = (1/√2)(|00⟩ - |11⟩)
|Ψ⁺⟩ = (1/√2)(|01⟩ + |10⟩)
|Ψ⁻⟩ = (1/√2)(|01⟩ - |10⟩)
```

**Creating Bell states from |00⟩**:

**|Φ⁺⟩ circuit**:
```
|0⟩ ──H──●──
         │
|0⟩ ─────⊕──

Result: (1/√2)(|00⟩ + |11⟩)
```

**|Φ⁻⟩ circuit**:
```
|0⟩ ──H──●──
         │
|0⟩ ──Z──⊕──

Result: (1/√2)(|00⟩ - |11⟩)
```

**|Ψ⁺⟩ circuit**:
```
|0⟩ ──H──●──
         │
|0⟩ ──X──⊕──

Result: (1/√2)(|01⟩ + |10⟩)
```

**|Ψ⁻⟩ circuit**:
```
|0⟩ ──H──●──
         │
|0⟩ ─XZ──⊕──

Result: (1/√2)(|01⟩ - |10⟩)
```

### 6.5 Complete Example: Bell State Creation

**Problem**: Create |Φ⁺⟩ starting from |00⟩

**Step-by-step**:
```
Initial: |ψ₀⟩ = |00⟩ = [1]
                        [0]
                        [0]
                        [0]

Step 1: Apply H⊗I
H⊗I = (1/√2)[1   1] ⊗ [1  0]
             [1  -1]   [0  1]

    = (1/√2)[1  0  1  0]
             [0  1  0  1]
             [1  0 -1  0]
             [0  1  0 -1]

|ψ₁⟩ = (H⊗I)|00⟩ = (1/√2)[1  0  1  0][1]   (1/√2)[1]
                           [0  1  0  1][0] =        [0]
                           [1  0 -1  0][0]          [1]
                           [0  1  0 -1][0]          [0]

     = (1/√2)(|00⟩ + |10⟩)

Step 2: Apply CNOT
|ψ₂⟩ = CNOT|ψ₁⟩ = (1/√2)(CNOT|00⟩ + CNOT|10⟩)
                 = (1/√2)(|00⟩ + |11⟩) = |Φ⁺⟩ ✓
```

**Matrix calculation**:
```
CNOT·(H⊗I) = [1  0  0  0]   (1/√2)[1  0  1  0]
             [0  1  0  0]          [0  1  0  1]
             [0  0  0  1]          [1  0 -1  0]
             [0  0  1  0]          [0  1  0 -1]

           = (1/√2)[1  0  1  0]
                   [0  1  0  1]
                   [0  1  0 -1]
                   [1  0 -1  0]

Final state:
|Φ⁺⟩ = (1/√2)[1  0  1  0][1]   (1/√2)[1]
              [0  1  0  1][0] =        [0]
              [0  1  0 -1][0]          [0]
              [1  0 -1  0][0]          [1]

     = (1/√2)|00⟩ + (1/√2)|11⟩ ✓
```

---

[← Previous](./05_*.md) | [Next →](./07_*.md)