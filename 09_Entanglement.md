# ## Chapter 9: Entanglement

### 9.1 What is Entanglement?

**Definition**: A state that cannot be written as a tensor product.

**Separable**:
```
|ψ⟩ = |ψ₁⟩ ⊗ |ψ₂⟩
```

**Entangled**: Not separable

### 9.2 Testing for Entanglement

**Method**: Try to factor the state.

**Example 1**: Is this entangled?
```
|ψ⟩ = (1/2)(|00⟩ + |01⟩ + |10⟩ + |11⟩)

Try factoring:
= (a|0⟩ + b|1⟩) ⊗ (c|0⟩ + d|1⟩)
= ac|00⟩ + ad|01⟩ + bc|10⟩ + bd|11⟩

We need:
ac = ad = bc = bd = 1/2

From ac = ad: c = d
From bc = bd: c = d ✓
From ac = bc: a = b

So a = b = c = d = 1/√2

Check: (1/√2)(|0⟩+|1⟩) ⊗ (1/√2)(|0⟩+|1⟩)
     = (1/2)(|00⟩ + |01⟩ + |10⟩ + |11⟩) ✓

NOT ENTANGLED (separable)
```

**Example 2**: Is this entangled?
```
|Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

Try factoring:
= (a|0⟩ + b|1⟩) ⊗ (c|0⟩ + d|1⟩)
= ac|00⟩ + ad|01⟩ + bc|10⟩ + bd|11⟩

We need:
ac = 1/√2
ad = 0
bc = 0
bd = 1/√2

From ad = 0: either a = 0 or d = 0
From bc = 0: either b = 0 or c = 0

Case 1: a = 0
Then ac = 0 ≠ 1/√2 ✗

Case 2: d = 0
Then bd = 0 ≠ 1/√2 ✗

Case 3: b = 0
Then bd = 0 ≠ 1/√2 ✗

Case 4: c = 0
Then ac = 0 ≠ 1/√2 ✗

CANNOT FACTOR → ENTANGLED!
```

### 9.3 Schmidt Decomposition

**Theorem**: Any pure state can be written as:
```
|ψ⟩ = Σᵢ λᵢ |iₐ⟩ ⊗ |iᵦ⟩
```

where λᵢ ≥ 0 and Σᵢ λᵢ² = 1

**Schmidt rank**: Number of non-zero λᵢ
- Rank 1: Separable
- Rank > 1: Entangled

**Example**: |Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

Already in Schmidt form:
λ₁ = 1/√2, |1ₐ⟩ = |0⟩, |1ᵦ⟩ = |0⟩
λ₂ = 1/√2, |2ₐ⟩ = |1⟩, |2ᵦ⟩ = |1⟩

Schmidt rank = 2 → Entangled

### 9.4 Correlations in Entanglement

**Bell state measurements**:

[← Previous](./08_*.md)