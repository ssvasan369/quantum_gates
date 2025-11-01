## Chapter 9: Entanglement

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

**Example**: |Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

Measure first qubit:
- Get 0 → second qubit must be 0
- Get 1 → second qubit must be 1
- **Perfect correlation!**

But:
- Before measurement: both qubits indefinite
- Measurement outcome: random (50/50)
- After first measurement: second qubit determined

**Example with numbers**:
```
Initial: |Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)

Alice measures her qubit:
- P(0) = 1/2, state becomes |00⟩
- P(1) = 1/2, state becomes |11⟩

Bob measures his qubit:
- If Alice got 0: Bob gets 0 with P=1
- If Alice got 1: Bob gets 1 with P=1

Results are correlated, but neither can control their outcome!
```

### 9.5 No-Cloning Theorem

**Statement**: Cannot create identical copy of unknown quantum state.

**Proof sketch**:
Suppose cloning operation U exists:
```
U(|ψ⟩ ⊗ |0⟩) = |ψ⟩ ⊗ |ψ⟩
```

For |0⟩:
```
U(|0⟩ ⊗ |0⟩) = |0⟩ ⊗ |0⟩
```

For |1⟩:
```
U(|1⟩ ⊗ |0⟩) = |1⟩ ⊗ |1⟩
```

For |+⟩ = (1/√2)(|0⟩ + |1⟩):
```
U(|+⟩ ⊗ |0⟩) = U[(1/√2)(|0⟩ + |1⟩) ⊗ |0⟩]
              = (1/√2)[U(|0⟩⊗|0⟩) + U(|1⟩⊗|0⟩)]  (linearity)
              = (1/√2)[|0⟩⊗|0⟩ + |1⟩⊗|1⟩]
```

But we wanted:
```
|+⟩ ⊗ |+⟩ = (1/2)(|00⟩ + |01⟩ + |10⟩ + |11⟩)
```

These are different! Contradiction. ✗

### 9.6 GHZ State (3-qubit entanglement)

```
|GHZ⟩ = (1/√2)(|000⟩ + |111⟩)
```

**Creating GHZ state**:
```
Circuit:
q₀: ──H──●────●──
         │    │
q₁: ─────⊕────┼──
              │
q₂: ──────────⊕──

Steps:
1. |000⟩
2. (H⊗I⊗I)|000⟩ = (1/√2)(|000⟩ + |100⟩)
3. CNOT₀₁: (1/√2)(|000⟩ + |110⟩)
4. CNOT₀₂: (1/√2)(|000⟩ + |111⟩) = |GHZ⟩
```

**Properties**:
- Measure q₀ as 0 → q₁ and q₂ both 0
- Measure q₀ as 1 → q₁ and q₂ both 1
- Three-way correlation

### 9.7 W State (Different type of 3-qubit entanglement)

```
|W⟩ = (1/√3)(|001⟩ + |010⟩ + |100⟩)
```

**Properties**:
- More robust to qubit loss than GHZ
- If one qubit lost, remaining two still entangled

**Difference from GHZ**:
```
Trace out one qubit from |GHZ⟩ → separable state
Trace out one qubit from |W⟩ → still entangled!
```

---