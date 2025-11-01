## Chapter 12: Advanced Topics

### 12.1 Density Matrices

**For mixed states** (statistical mixtures):
```
ρ = Σᵢ pᵢ |ψᵢ⟩⟨ψᵢ|
```

where pᵢ ≥ 0 and Σᵢ pᵢ = 1

**Example**: Classical mixture of |0⟩ and |1⟩
```
ρ = 0.6|0⟩⟨0| + 0.4|1⟩⟨1|

= 0.6[1][1  0] + 0.4[0][0  1]
     [0]          [1]

= 0.6[1  0] + 0.4[0  0]  = [0.6  0  ]
     [0  0]      [0  1]    [0    0.4]
```

**Pure state**: ρ = |ψ⟩⟨ψ|, has ρ² = ρ

**Example**:
```
|+⟩⟨+| = [(1/√2)][1/√2  1/√2]  = (1/2)[1  1]
         [(1/√2)]                      [1  1]

Check: ρ² = (1/4)[1  1][1  1] = (1/4)[2  2] = (1/2)[1  1] = ρ ✓
                 [1  1][1  1]        [2  2]        [1  1]
```

### 12.2 Partial Trace

**Removing a subsystem**: Trace out unwanted qubits

**Definition**:
```
ρ_A = Tr_B(ρ_AB)
```

**Example**: Trace out second qubit of |Φ⁺⟩
```
|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

ρ_AB = |Φ⁺⟩⟨Φ⁺| = (1/2)(|00⟩⟨00| + |00⟩⟨11| + |11⟩⟨00| + |11⟩⟨11|)

ρ_A = Tr_B(ρ_AB) = (1/2)(⟨0|00⟩⟨00|0⟩ + ⟨1|00⟩⟨00|1⟩ 
                        + ⟨0|00⟩⟨11|0⟩ + ⟨1|00⟩⟨11|1⟩
                        + ⟨0|11⟩⟨00|0⟩ + ⟨1|11⟩⟨00|1⟩
                        + ⟨0|11⟩⟨11|0⟩ + ⟨1|11⟩⟨11|1⟩)

    = (1/2)(|0⟩⟨0| + |1⟩⟨1|) = (1/2)I

This is maximally mixed! (signature of entanglement)
```

### 12.3 Fidelity

**Measuring closeness** of quantum states:
```
F(ρ, σ) = [Tr√(√ρ σ √ρ)]²
```

**For pure states**: F(|ψ⟩, |φ⟩) = |⟨ψ|φ⟩|²

**Example**:
```
|ψ⟩ = |0⟩
|φ⟩ = (1/√2)(|0⟩ + |1⟩) = |+⟩

F = |⟨0|+⟩|² = |(1/√2)|² = 1/2

States are 50% similar
```

**Example 2**: Orthogonal states
```
F(|0⟩, |1⟩) = |⟨0|1⟩|² = 0

Completely different states
```

### 12.4 Quantum Gates on Density Matrices

**Evolution**:
```
ρ → UρU†
```

**Example**: X gate on mixed state
```
ρ = (1/2)[1  0]  (50% |0⟩, 50% |1⟩)
          [0  1]

XρX† = [0  1][(1/2)[1  0]][0  1]
       [1  0]       [0  1] [1  0]

     = [0  1][(1/2)[1  0]]
       [1  0]       [0  1]

     = (1/2)[0  1][1  0] = (1/2)[0  1] = (1/2)[1  0]
            [1  0][0  1]        [1  0]        [0  1]

Same state! (X swaps populations)
```

### 12.5 Quantum Error

**Pauli error channel**: Errors X, Y, Z with probabilities

**Example**: Bit flip with probability p
```
ε(ρ) = (1-p)ρ + p·XρX†
```

**Depolarizing channel**:
```
ε(ρ) = (1-p)ρ + (p/3)(XρX† + YρY† + ZρZ†)
```

**Example calculation**:
```
Initial: ρ = |0⟩⟨0| = [1  0]
                      [0  0]

After depolarizing with p=0.1:
ε(ρ) = 0.9[1  0] + (0.1/3)([0  0] + [0  0] + [1   0])
           [0  0]            [0  1]   [0  1]   [0  -1]

     = 0.9[1  0] + (0.1/3)[1  -1]
           [0  0]           [-1  1]

     ≈ [0.933  -0.033]
       [-0.033  0.033]
```

### 12.6 Quantum Process Tomography

**Goal**: Fully characterize unknown quantum gate

**Method**: 
1. Prepare input states (e.g., |0⟩, |1⟩, |+⟩, |+i⟩)
2. Apply unknown gate U
3. Measure output in different bases
4. Reconstruct U from data

**Example**: 1-qubit gate needs 4 input states × 3 measurement bases = 12 measurements

### 12.7 Quantum Circuit Complexity

**Gate count**: Number of gates in circuit

**Example**: Creating |+⟩ⁿ
```
Circuit: Apply H to each of n qubits
Gate count: n

|0⟩─H─
|0⟩─H─
...
|0⟩─H─
```

**Depth**: Number of time steps (parallel gates count as 1 step)

**Example**:
```
Circuit 1: X─X─X─  (Depth = 3)

Circuit 2: X─     (Depth = 1)
           X─     All gates in parallel
           X─
```

### 12.8 Variational Quantum Algorithms

**Structure**: Parameterized circuit + classical optimization

**Example**: Variational Quantum Eigensolver (VQE)

```
1. Prepare: |ψ(θ)⟩ using gates with parameters θ
2. Measure: ⟨ψ(θ)|H|ψ(θ)⟩ (expectation of Hamiltonian)
3. Optimize: Update θ to minimize energy
4. Repeat until convergence
```

**Sample circuit**:
```
|0⟩─Ry(θ₁)─●─────Ry(θ₃)─
           │
|0⟩─Ry(θ₂)─⊕─────Ry(θ₄)─
```

Parameters θ₁, θ₂, θ₃, θ₄ optimized classically.

### 12.9 Quantum Supremacy Circuits

**Random circuits**: Hard to simulate classically

**Example structure**:
```
Layer 1: Random single-qubit rotations
Layer 2: Random CNOT pattern
Layer 3: Random single-qubit rotations
Layer 4: Random CNOT pattern
...
Repeat for many layers
```

**Key property**: Creates highly entangled state that's difficult to compute classically

### 12.10 Practical Implementation Example

**Problem**: Implement 3-qubit Deutsch-Jozsa algorithm

**Goal**: Determine if f:{0,1}³→{0,1} is constant or balanced

**Circuit**:
```
|0⟩─H─────────●──────H─M─
              │
|0⟩─H─────────┼──●───H─M─
              │  │
|0⟩─H─────────┼──┼──●─H─M─
              │  │  │
|1⟩─H──[f]────⊕──⊕──⊕────

where [f] is the oracle for function f
```

**Complete steps**:

1. **Initialize**: |0⟩|0⟩|0⟩|1⟩

2. **Apply H⊗⁴**:
```
(1/4)(|0⟩+|1⟩)⊗(|0⟩+|1⟩)⊗(|0⟩+|1⟩)⊗(|0⟩-|1⟩)
= (1/4)Σₓ|x⟩ ⊗ (|0⟩-|1⟩)
```

3. **Apply oracle**: (phase kickback)
```
→ (1/4)Σₓ(-1)^f(x)|x⟩ ⊗ (|0⟩-|1⟩)
```

4. **Apply H⊗³ to first 3 qubits**: Interference!

5. **Measure**: 
   - All 0: f is constant
   - Any 1: f is balanced

**Example oracle** for f(x) = x₁ ⊕ x₂:
```
CNOT₀₃ · CNOT₁₃
```

This completes our comprehensive guide through quantum gates and circuits!

---

## Appendix: Quick Reference

### Common Single-Qubit Gates
```
I = [1  0]    X = [0  1]    Y = [0  -i]    Z = [1   0]
    [0  1]        [1  0]        [i   0]        [0  -1]

H = (1/√2)[1   1]    S = [1  0]    T = [1      0     ]
           [1  -1]        [0  i]        [0  e^(iπ/4) ]
```

### Common Two-Qubit Gates
```
CNOT = [1  0  0  0]    CZ = [1  0  0   0]    SWAP = [1  0  0  0]
       [0  1  0  0]         [0  1  0   0]           [0  0  1  0]
       [0  0  0  1]         [0  0  1   0]           [0  1  0  0]
       [0  0  1  0]         [0  0  0  -1]           [0  0  0  1]
```

### Key Formulas
```
Normalization: |α|² + |β|² = 1
Unitarity: U†U = I
Inner product: ⟨ψ|φ⟩ = Σᵢ ψᵢ*φᵢ
Measurement probability: P(i) = |αᵢ|²
Expected value: ⟨A⟩ = ⟨ψ|A|ψ⟩
```

### Important Identities
```
HXH = Z
HZH = X
XX = YY = ZZ = I
XY = iZ
[X,Z] = 2iY
```