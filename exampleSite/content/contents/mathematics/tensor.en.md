---
title: Tensor
description: "Tensor and tensor field"
params:
  math: true
---

# Understanding Rank-\((k,l)\) Tensors

In differential geometry and multilinear algebra, you often see **\((k,l)\)-tensors**—sometimes also called “rank-\((k,l)\) tensors.” But what does this notation really mean, and why is there confusion about something like a \((1,0)\)-tensor?

This post aims to **clear up** common misunderstandings about how **vectors** and **covectors** relate to **\((k,l)\)-tensor** notation.

---

## 1. Basic Definition

A **\((k,l)\)-tensor** on a vector space \(V\) over a field \(\mathbf{F}\) (usually \(\mathbf{R}\) or \(\mathbf{C}\)) is a multilinear map

\[
T:\; 
\underbrace{(V^*) \times \cdots \times (V^*)}_{k\text{ times}}
\;\times\;
\underbrace{V \times \cdots \times V}_{l\text{ times}}
\;\longrightarrow\;\mathbf{F}.
\]

- **Multilinear** means linear in each argument when the others are held fixed.  
- **\(V^*\)** is the **dual space** (covectors), i.e. all linear maps \(V \to \mathbf{F}\).  
- The integers \(k\) and \(l\) track how many slots expect covectors vs. vectors.

### Why “\((k,l)\) Tensor”?

- \(k\) is sometimes called the **contravariant rank** (associated with **upper** indices when you write components).  
- \(l\) is the **covariant rank** (associated with **lower** indices).

In older texts, people might say “rank-\((k,l)\) object” to emphasize it has a total of \(k+l\) slots—\(k\) for covectors, \(l\) for vectors.

---

## 2. Key Examples

### (0,1)-Tensor = Covector
A **\((0,1)\)-tensor** takes **one vector** and returns a scalar. Symbolically,

\[
T: V \;\longrightarrow\;\mathbf{F}.
\]

In standard language, that’s just a **covector** (or 1-form). For example, a linear functional \(\omega(v) = \alpha \, x\text{-component} + \cdots\) belongs to \(V^*\).

### (1,0)-Tensor = Vector
A **\((1,0)\)-tensor** takes **one covector** and returns a scalar:

\[
T: V^* \;\longrightarrow\;\mathbf{F}.
\]

But any linear map \(\phi: V^* \to \mathbf{F}\) can be identified with a vector in \(V\) itself (via the **double dual** isomorphism \((V^*)^* \cong V\) for finite-dimensional \(V\)).  

This is why a \((1,0)\)-tensor is essentially the same thing as a **vector**.

### (0,2)-Tensor = Bilinear Form on V
A **\((0,2)\)-tensor** takes **two vectors** as input and returns a real number:

\[
T: V \times V \;\longrightarrow\;\mathbf{R}.
\]

A classic example is the **dot product** or **any** bilinear form:

\[
T(\mathbf{v}, \mathbf{w}) 
\;=\; 
g_{ij}\,v^i\,w^j
\]
(in coordinates), which is linear in both \(\mathbf{v}\) and \(\mathbf{w}\).

### (2,2)-Tensor
A **\((2,2)\)-tensor** takes **two covectors** and **two vectors**, returning a scalar:

\[
T: (V^*)^2 \times V^2 \;\longrightarrow\;\mathbf{R}.
\]

An explicit example:
\[
T(\alpha, \beta;\; \mathbf{v}, \mathbf{w}) \;=\; \alpha(\mathbf{v}) \,\beta(\mathbf{w}).
\]
Each pair \(\bigl(\alpha(\mathbf{v}), \beta(\mathbf{w})\bigr)\) is a pair of real numbers, and we multiply them.

---

## 3. Why the Confusion?

1. **Mismatch of “slots” vs. “type”**  
   - It’s natural to think “\((k,l)\) = k \text{ vectors} + l \text{ covectors}.” But in the formal definition, **\(k\) is the number of covector inputs** (\(V^*\)) and **\(l\) is the number of vector inputs** (\(V\)).  
   - This can feel reversed if you’re not used to contravariant vs. covariant labeling.

2. **“(1,0)” vs. “1 slot for a vector?”**  
   - Actually, \((1,0)\) means “1 contravariant slot,” which is an input from **\(V^*\)**, not \(V\). Since it eats a covector, it corresponds to something isomorphic to a vector in \(V\).  
   - Conversely, \((0,1)\) means “1 covariant slot,” an input from \(V\), so that’s a covector.

3. **Rank in Tensors vs. Rank in Matrices**  
   - The word “rank” also appears in matrix theory to mean “dimension of the image space.” That’s **completely different** from “rank-\((k,l)\).”

---

## 4. Summary Table

| **Tensor Type** | **Formal Definition** | **Isomorphic To**           | **Example**                                  |
|:---------------:|:---------------------:|:---------------------------:|:-------------------------------------------:|
| \((0,0)\)       | Map with no inputs    | Scalar (real number)        | Just a real number                          |
| \((0,1)\)       | \(V \to \mathbb{R}\)  | Covector (1-form)           | Linear functional \(\omega(\mathbf{v})\)    |
| \((1,0)\)       | \(V^* \to \mathbb{R}\)| Vector (via double-dual)    | \(\phi(\alpha)\), \(\alpha\in V^*\)         |
| \((0,2)\)       | \(V\times V\to \mathbb{R}\) | Bilinear form       | Dot product, metric, etc.                  |
| \((1,1)\)       | \(V^*\times V\to \mathbb{R}\) | Linear map \(V\to V\) | “Matrix” in coordinate representation       |
| \((2,2)\)       | \((V^*)^2 \times V^2 \to \mathbb{R}\)| More complex | E.g. \(T(\alpha,\beta;\mathbf{v},\mathbf{w})=\alpha(\mathbf{v})\beta(\mathbf{w})\) |

---

## 5. Take-Home Points

1. **\((k,l)\)-tensor** means \(k\) inputs from \(V^*\) (covectors) and \(l\) inputs from \(V\) (vectors).  
2. **“\((1,0)\)-tensor” is a vector**, because it’s a map \(V^* \to \mathbb{R}\) and via \((V^*)^* \cong V\), it identifies with a single vector in \(V\).  
3. **“\((0,1)\)-tensor” is a covector**, i.e. a 1-form.  
4. The word “**rank**” here is about the number of contravariant and covariant slots, **not** the same as “matrix rank.”  
5. Coordinate expressions often use **upper indices** to represent covariant slots and **lower indices** to represent vector slots, which can feel reversed to the uninitiated.

---

# Final Thoughts

Whenever you see **rank-\((k,l)\) tensors**:

- Remember the definition: they’re multilinear maps with \(k\) inputs from \(V^*\) and \(l\) inputs from \(V\).  
- Resist the initial urge to count “(1,0) means 1 vector slot.” Actually, the “1” indicates a slot for a **covector** (which makes the tensor correspond to a vector).  

With this perspective, you’ll navigate tensor notation far more confidently!

