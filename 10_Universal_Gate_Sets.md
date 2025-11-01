## Chapter 10: Universal Gate Sets

### 10.1 What is Universality?

**Definition**: A gate set is **universal** if any unitary operation can be approximated arbitrarily well using gates from the set.

**Why important**: 
- Build any quantum algorithm
- Practical: implement subset of gates in hardware

### 10.2 Single-Qubit Universality

**Theorem**: Any single-qubit unitary can be decomposed as:
```
U = e^(iα) Rz(β) Ry(γ) Rz(δ)
```

**Example**: Decompose Hadamard
```
H = e^(iπ/2) Rz(π) Ry(π/2) Rz(0)

Verify:
Rz(π) = [e^(-iπ/2)    0      ]  = [-i   0]
        [0         e^(iπ/2) ]    [0    i]

Ry(π/2) = [cos(π/4)  -sin(π/4)]  = [1/√2  -1/√2]
          [sin(π/4)   cos(π/4)]    [1/√2   1/√2]

Rz(π)Ry(π/2) = [-i   0][1/√2  -1/√2]  = [-i/√2   i/√2]
               [0    i][1/√2   1/√2]    [i/√2    i/√2]

Times e^(iπ/2) = i:
i·[-i/√2   i/√2]  = [1/√2   -1/√2]  ≈ H (up to global phase)
  [i/√2    i/√2]    [1/√2    1/√2]
```

### 10.3 Two-Level Universality

**Theorem**: {Single-qubit gates, CNOT} is universal for quantum computation.

**Reason**: Can build any multi-qubit gate

**Example**: Build SWAP from CNOTs
```
SWAP = CNOT₁₂ · CNOT₂₁ · CNOT₁₂

Verify on |01⟩:
|01⟩ → CNOT₁₂ → |01⟩ (control=0, no change)
     → CNOT₂₁ → |11⟩ (control=1, flip first)
     → CNOT₁₂ → |10⟩ (control=1, flip second)

|01⟩ → |10⟩ ✓ (swapped!)
```

### 10.4 Discrete Universal Sets

**Clifford + T**: {H, S, CNOT, T} is universal

Where:
```
H = (1/√2)[1   1]
           [1  -1]

S = [1  0]
    [0  i]

T = [1      0     ]
    [0  e^(iπ/4) ]
```

**Why useful**: All gates except T are "easy" (can be simulated classically)
T gate provides "quantum power"

**Example**: Approximate any rotation using H, S, T
```
Rx(θ) ≈ sequence of H, S, T gates

For θ = π/8:
Rx(π/8) ≈ H T H T† H
```

### 10.5 Solovay-Kitaev Theorem

**Statement**: Any single-qubit gate can be approximated to precision ε using O(log^c(1/ε)) gates from a universal set.

**Example**:
```
Want: U with error < 0.001
Need: ~log⁴(1000) ≈ 100 gates

Want: error < 0.000001  
Need: ~log⁴(1000000) ≈ 400 gates

Efficient scaling!
```

### 10.6 Example: Toffoli Gate from Universal Set

**Toffoli** (CCNOT): 3-qubit gate, flips target if both controls are 1

**Decomposition** using CNOT and single-qubit gates:
```
CCNOT can be built from 6 CNOTs and several T, T†, H gates

Circuit (simplified):
q₀: ──●────────●──T†─●────●──T†──●──
      │        │     │    │      │
q₁: ──┼──●─────┼──T──┼──●─┼──T†──┼──●──T──
      │  │     │     │  │ │      │  │
q₂: ──⊕──┼──T──⊕─────⊕──┼─⊕──T†──⊕──┼──T──H──
         │                │           │
        (H, T gates on target)
```

---