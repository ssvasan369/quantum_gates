# ## Chapter 2: Classical vs Quantum Bits

### 2.1 Classical Bit

A classical bit has two states: **0** or **1**

**Properties**:
- Deterministic: always in a definite state
- Can be copied
- Measurement doesn't change the state

**Logic gates** (NOT):
```
Input: 0  →  Output: 1
Input: 1  →  Output: 0
```

### 2.2 Quantum Bit (Qubit) - Intuitive Introduction

A qubit can be in a **superposition** of 0 and 1.

**Key difference**:
```
Classical: [0] OR [1]
Quantum:   α[0] + β[1]   where α,β are complex numbers
```

**Example**:
```
|ψ⟩ = (1/√2)|0⟩ + (1/√2)|1⟩

This qubit is "half 0 and half 1" simultaneously
```

**Properties**:
- Can exist in superposition
- Cannot be cloned (no-cloning theorem)
- Measurement changes the state (collapses superposition)

### 2.3 Why Complex Numbers?

Quantum mechanics requires:
1. **Superposition**: combining states
2. **Interference**: waves can cancel or amplify
3. **Phase**: relative timing matters

Complex numbers provide:
- Magnitude: probability amplitude
- Phase: for interference

**Example**:
```
|ψ⟩ = (1/√2)|0⟩ + (1/√2)|1⟩        (in phase)
|φ⟩ = (1/√2)|0⟩ - (1/√2)|1⟩        (out of phase)

These are different quantum states!
```

---

[← Previous](./01_*.md) | [Next →](./03_*.md)