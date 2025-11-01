## Chapter 7: Quantum Circuits

### 7.1 Circuit Notation

**Components**:
- Horizontal lines: qubits (time flows left to right)
- Boxes: single-qubit gates
- Connected symbols: multi-qubit gates
- Meter symbol: measurement

**Example circuit**:
```
q₀: ──H──●─────M
         │
q₁: ─────⊕──H──M
```

### 7.2 Sequential Gate Application

Gates are applied from **left to right**.

**Mathematical form**: For circuit with gates U₁, U₂, U₃:
```
|ψ_final⟩ = U₃ · U₂ · U₁ · |ψ_initial⟩
```

**Example 1**: Simple sequence
```
Circuit: |0⟩──H──X──H──

|ψ₀⟩ = |0⟩
|ψ₁⟩ = H|0⟩ = (1/√2)(|0⟩ + |1⟩)
|ψ₂⟩ = X|ψ₁⟩ = (1/√2)(|1⟩ + |0⟩) = |ψ₁⟩
|ψ₃⟩ = H|ψ₂⟩ = |0⟩
```

**Matrix form**:
```
U_total = H·X·H

H·X = (1/√2)[1   1][0  1] = (1/√2)[1  1]
             [1  -1][1  0]          [-1 1]

H·X·H = (1/√2)[1   1]·(1/√2)[1   1]
               [1  -1]        [1  -1]

      = (1/2)[2   0] = [1  0]
             [0  -2]   [0 -1] = Z
```

So the circuit is equivalent to Z gate!

**Example 2**: Two-qubit circuit
```
Circuit:
q₀: ──H──●──H──
         │
q₁: ─────⊕─────

Step by step:
|ψ₀⟩ = |00⟩
|ψ₁⟩ = (H⊗I)|00⟩ = (1/√2)(|00⟩ + |10⟩)
|ψ₂⟩ = CNOT|ψ₁⟩ = (1/√2)(|00⟩ + |11⟩)
|ψ₃⟩ = (H⊗I)|ψ₂⟩ = ?

Let's calculate:
(H⊗I)|00⟩ = |+0⟩ = (1/√2)(|00⟩ + |10⟩)
(H⊗I)|11⟩ = |−1⟩ = (1/√2)(|01⟩ - |11⟩)

|ψ₃⟩ = (1/√2)[(1/√2)(|00⟩+|10⟩) + (1/√2)(|01⟩-|11⟩)]
     = (1/2)(|00⟩ + |10⟩ + |01⟩ - |11⟩)
```

### 7.3 Parallel Gates

Gates on different qubits can be applied simultaneously.

**Notation**:
```
q₀: ──U──
q₁: ──V──

Combined operation: U ⊗ V
```

**Example**:
```
Circuit:
q₀: ──H──
q₁: ──X──

|00⟩ → (H⊗X)|00⟩ = (H|0⟩) ⊗ (X|0⟩)
                  = |+⟩ ⊗ |1⟩
                  = (1/√2)(|01⟩ + |11⟩)
```

### 7.4 Quantum Teleportation Circuit

**Goal**: Transfer quantum state from Alice to Bob using entanglement

**Circuit**:
```
      ┌───┐     ┌─┐
|ψ⟩ ──┤ ├──●──┤M├─────────╮
      └───┘  │  └─┘         │
|0⟩ ──H────⊕────┤M├──╮      │
                 └─┘  │      │
|0⟩ ─────────────────┼──X───Z──
                      ↓      ↓
                    (if M=1)(if M=1)
```

**Step-by-step**:

1. **Initial state**: |ψ⟩ = α|0⟩ + β|1⟩ (to be teleported)

2. **Create Bell pair** (qubits 2-3):
   ```
   |Φ⁺⟩ = (1/√2)(|00⟩ + |11⟩)
   ```

3. **Combined state**:
   ```
   (α|0⟩ + β|1⟩) ⊗ (1/√2)(|00⟩ + |11⟩)
   = (1/√2)[α|000⟩ + α|011⟩ + β|100⟩ + β|111⟩]
   ```

4. **Apply CNOT** (qubits 1-2):
   ```
   (1/√2)[α|000⟩ + α|011⟩ + β|110⟩ + β|101⟩]
   ```

5. **Apply H** (qubit 1):
   ```
   (1/2)[α(|0⟩+|1⟩)|00⟩ + α(|0⟩+|1⟩)|11⟩ 
        + β(|0⟩-|1⟩)|10⟩ + β(|0⟩-|1⟩)|01⟩]
   
   = (1/2)[|00⟩(α|0⟩+β|1⟩) + |01⟩(α|1⟩+β|0⟩)
         + |10⟩(α|0⟩-β|1⟩) + |11⟩(α|1⟩-β|0⟩)]
   ```

6. **Measure qubits 1,2**: Get one of |00⟩, |01⟩, |10⟩, |11⟩

7. **Apply corrections** to qubit 3:
   - If |00⟩: do nothing → α|0⟩ + β|1⟩ ✓
   - If |01⟩: apply X → α|0⟩ + β|1⟩ ✓
   - If |10⟩: apply Z → α|0⟩ + β|1⟩ ✓
   - If |11⟩: apply XZ → α|0⟩ + β|1⟩ ✓

Result: |ψ⟩ successfully teleported!

### 7.5 Quantum Fourier Transform (QFT)

**For n qubits**, QFT maps:
```
|j⟩ → (1/√N) Σₖ e^(2πijk/N) |k⟩  where N = 2ⁿ
```

**One-qubit QFT** (just Hadamard):
```
|0⟩ → (1/√2)(|0⟩ + |1⟩)
|1⟩ → (1/√2)(|0⟩ - |1⟩)
```

**Two-qubit QFT circuit**:
```
q₀: ──H──●─────SWAP──
         │P(π/2)
q₁: ─────●────H─SWAP──
```

**Example calculation** for |00⟩:
```
Step 1: H on q₀
|00⟩ → (1/√2)(|00⟩ + |10⟩)

Step 2: Controlled-Phase(π/2)
→ (1/√2)(|00⟩ + i|10⟩)  (no effect since q₁=0)
Actually: (1/√2)(|00⟩ + |10⟩)  unchanged

Step 3: H on q₁
→ (1/2)(|00⟩ + |01⟩ + |10⟩ + |11⟩)

Step 4: SWAP
→ (1/2)(|00⟩ + |10⟩ + |01⟩ + |11⟩)

This is the QFT of |00⟩!
```

### 7.6 Circuit Identities and Simplification

**Identity 1**: HXH = Z
```
Proof:
HXH|0⟩ = HX|+⟩ = H|−⟩ = |0⟩ = Z|0⟩
HXH|1⟩ = HX|−⟩ = -H|+⟩ = -|1⟩ = Z|1⟩
```

**Identity 2**: Double negation
```
XX = I
```

**Identity 3**: Hadamard self-inverse
```
HH = I
```

**Identity 4**: Phase relationships
```
SS = Z
SSSS = I
```

**Example**: Simplify circuit
```
Original: |0⟩──H──X──X──H──

Simplify XX = I:
|0⟩──H──I──H──

Simplify HH = I:
|0⟩──I── = |0⟩

The circuit does nothing!
```

---