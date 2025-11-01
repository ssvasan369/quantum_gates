## Chapter 1: Mathematical Prerequisites

### 1.1 Complex Numbers

Complex numbers are essential for quantum mechanics.

**Definition**: A complex number z = a + bi where:
- a is the real part: Re(z) = a
- b is the imaginary part: Im(z) = b
- i is the imaginary unit: i² = -1

**Polar form**: z = r·e^(iθ) = r(cos θ + i sin θ)
- r = |z| = √(a² + b²) is the magnitude
- θ = arg(z) = arctan(b/a) is the phase

**Example**:
```
z = 3 + 4i
|z| = √(3² + 4²) = 5
θ = arctan(4/3) ≈ 53.13°
z = 5·e^(i·53.13°)
```

**Complex conjugate**: z* = a - bi
```
If z = 3 + 4i, then z* = 3 - 4i
z·z* = (3+4i)(3-4i) = 9 + 16 = 25 = |z|²
```

### 1.2 Vector Spaces

A **vector space** V over complex numbers ℂ has:
- Vectors that can be added
- Vectors that can be multiplied by scalars (complex numbers)

**Example**: ℂ² (2-dimensional complex vectors)
```
v = [3 + 2i]
    [1 - i ]
```

### 1.3 Inner Product (Dot Product)

For vectors u, v in ℂⁿ:
```
⟨u|v⟩ = Σᵢ uᵢ* vᵢ
```

**Example**:
```
u = [1+i]    v = [2  ]
    [2  ]        [3-i]

⟨u|v⟩ = (1+i)*·2 + 2*·(3-i)
      = (1-i)·2 + 2·(3-i)
      = 2 - 2i + 6 - 2i
      = 8 - 4i
```

**Norm** (length): ||v|| = √⟨v|v⟩

**Example**:
```
v = [3]
    [4]

||v|| = √(3² + 4²) = √25 = 5
```

### 1.4 Matrices

A matrix is a rectangular array of numbers.

**Example**: 2×2 matrix
```
A = [a  b]
    [c  d]
```

**Matrix multiplication**:
```
[a  b] [e]   [ae + bf]
[c  d] [f] = [ce + df]
```

**Example**:
```
[1  2] [5]   [1·5 + 2·6]   [17]
[3  4] [6] = [3·5 + 4·6] = [39]
```

**Identity matrix** I:
```
I = [1  0]
    [0  1]
```

**Transpose** A^T: rows become columns
```
If A = [1  2]    then A^T = [1  3]
       [3  4]                [2  4]
```

**Conjugate transpose** (Hermitian conjugate) A†:
```
If A = [1+i   2]    then A† = [1-i    3-i]
       [3+i   4]                [2      4  ]
```

### 1.5 Dirac Notation (Bra-Ket)

**Ket** |ψ⟩: a column vector
```
|ψ⟩ = [α]
      [β]
```

**Bra** ⟨ψ|: a row vector (conjugate transpose of ket)
```
⟨ψ| = [α*  β*]
```

**Inner product**: ⟨φ|ψ⟩
```
⟨φ|ψ⟩ = [α*  β*] [γ]  = α*γ + β*δ
                  [δ]
```

**Outer product**: |ψ⟩⟨φ| (creates a matrix)
```
|ψ⟩⟨φ| = [α] [γ*  δ*] = [αγ*  αδ*]
         [β]             [βγ*  βδ*]
```

---