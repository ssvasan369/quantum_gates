# ## Chapter 8: Measurement Theory

### 8.1 Computational Basis Measurement

**Born rule**: Probability of measuring |i⟩ is |αᵢ|²

**Example 1**: Simple measurement
```
|ψ⟩ = (3/5)|0⟩ + (4/5)|1⟩

P(0) = |3/5|² = 9/25 = 0.36
P(1) = |4/5|² = 16/25 = 0.64
```

**Example 2**: With phase
```
|ψ⟩ = (1/√2)|0⟩ + (i/√2)|1⟩

P(0) = |1/√2|² = 1/2
P(1) = |i/√2|² = |i|²/2 = 1/2

Phase doesn't affect measurement probabilities!
```

**Example 3**: Bell state
```
|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

P(00) = |1/√2|² = 1/2
P(01) = |0|² = 0
P(10) = |0|² = 0
P(11) = |1/√2|² = 1/2

Measuring both qubits: 50% chance of 00, 50% chance of 11
```

### 8.2 Post-Measurement State

**Collapse**: After measurement, state becomes the measured basis state.

**Example**:
```
Before: |ψ⟩ = (3/5)|0⟩ + (4/5)|1⟩

Measure and get 0:
After: |ψ'⟩ = |0⟩

Measure and get 1:
After: |ψ'⟩ = |1⟩
```

### 8.3 Partial Measurement

**Measuring one qubit** in a multi-qubit system.

**Example**: Measure first qubit of |Φ⁺⟩
```
|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

If measure q₀ and get 0:
- State becomes |00⟩
- Probability: 1/2

If measure q₀ and get 1:
- State becomes |11⟩
- Probability: 1/2
```

**General procedure**:
1. Project onto measurement outcome
2. Renormalize

**Example**:
```
|ψ⟩ = (1/√3)|00⟩ + (1/√3)|01⟩ + (1/√3)|10⟩

Measure q₀:

P(q₀=0) = |1/√3|² + |1/√3|² = 2/3
State after: [(1/√3)|00⟩ + (1/√3)|01⟩]/√(2/3)
           = (1/√2)|00⟩ + (1/√2)|01⟩
           = |0⟩ ⊗ |+⟩

P(q₀=1) = |1/√3|² = 1/3
State after: (1/√3)|10⟩/√(1/3) = |10⟩ = |1⟩ ⊗ |0⟩
```

### 8.4 Measurement in Different Bases

**Measurement operator**: M = Σᵢ |bᵢ⟩⟨bᵢ|

**Example**: Measure |ψ⟩ = (3/5)|0⟩ + (4/5)|1⟩ in {|+⟩, |−⟩} basis

First, express |ψ⟩ in new basis:
```
|0⟩ = (1/√2)(|+⟩ + |−⟩)
|1⟩ = (1/√2)(|+⟩ - |−⟩)

|ψ⟩ = (3/5)(1/√2)(|+⟩+|−⟩) + (4/5)(1/√2)(|+⟩-|−⟩)
    = (1/√2)[(3/5 + 4/5)|+⟩ + (3/5 - 4/5)|−⟩]
    = (7/5√2)|+⟩ - (1/5√2)|−⟩

P(+) = |7/5√2|² = 49/50
P(−) = |1/5√2|² = 1/50
```

### 8.5 Expected Values

**Observable**: Hermitian matrix A
**Expected value**: ⟨A⟩ = ⟨ψ|A|ψ⟩

**Example**: Measure Z on |+⟩
```
|+⟩ = (1/√2)|0⟩ + (1/√2)|1⟩

Z = [1   0]
    [0  -1]

⟨Z⟩ = ⟨+|Z|+⟩
    = [(1/√2)  (1/√2)][1   0][(1/√2)]
                        [0  -1][(1/√2)]
    
    = [(1/√2)  (1/√2)][(1/√2) ]
                       [-(1/√2)]
    
    = (1/√2)·(1/√2) + (1/√2)·(-(1/√2))
    = 1/2 - 1/2 = 0
```

**Interpretation**: On average, measuring Z on |+⟩ gives 0.

**Verification**:
```
P(+1) = P(|0⟩) = 1/2  (eigenvalue +1)
P(-1) = P(|1⟩) = 1/2  (eigenvalue -1)

Average = (+1)·(1/2) + (-1)·(1/2) = 0 ✓
```

---

[← Previous](./07_*.md) | [Next →](./09_*.md)