<img width="1792" height="595" alt="image" src="https://github.com/user-attachments/assets/cb8cb3ef-09bc-408e-a78d-ce7faf4b3c86" /># Digital Techniques Sessional — Lab Report 02

**Course No:** ECE 2112
**Report Title:** Simplification of Boolean Expressions Using Boolean Algebra and Karnaugh Map, and Verification Using Logic Circuit Simulation
**Date of Submission:** 3 August, 2026

**Submitted By:** Zubaer Ahmed Siam, Roll: 2410020, Department of Electrical & Computer Engineering
**Submitted To:** MST. Mazeda Noor Tasnim, Lecturer, Department of Electrical & Computer Engineering, RUET

---

## Problem 1: Boolean Simplification

### Problem Definition
Simplify the Boolean expression F(A, B, C) = A′BC + AB′C + ABC′ + ABC using Boolean algebra and the Karnaugh map, and verify both the original and simplified circuits through logic simulation.

### Objective
To reduce a three-variable sum-of-minterms expression to its minimal sum-of-products form, to confirm this reduction with a Karnaugh map, and to check that the original and simplified circuits behave identically by building both in Logisim.

### Algebraic Simplification

```
F(A, B, C) = A′BC + AB′C + ABC′ + ABC
           = A′BC + ABC + AB′C + ABC + ABC′ + ABC
           = BC(A′ + A) + AC(B′ + B) + AB(C′ + C)
           = BC + AC + AB
           = AB + AC + BC
```

### Truth Table

| A | B | C | F = AB + AC + BC |
|---|---|---|-------------------|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

### Karnaugh Map

| A \ BC | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| 0      | 0  | 0  | 1  | 0  |
| 1      | 0  | 1  | 1  | 1  |

Three pairs of adjacent 1-cells can be grouped: the pair at BC = 11 across both rows gives BC; the pair where A = 1 and C = 1 (columns BC = 01, 11) gives AC; and the pair where A = 1 and B = 1 (BC = 11, 10) gives AB. Together these three groups produce the minimized expression F = AB + AC + BC, which agrees with the algebraic derivation.

### Circuit Diagram

<img width="1792" height="595" alt="image" src="https://github.com/user-attachments/assets/ee525cb7-3336-47c3-a11e-0ba5aeffa078" />


**Figure 1:** Original circuit (four 3-input AND gates and a 3-input OR gate realizing A′BC + AB′C + ABC′ + ABC) alongside the simplified circuit (three 2-input AND gates and an OR gate realizing AB + AC + BC), both simulated in Logisim.

### Discussion
The original circuit implements the expression exactly as written, needing four 3-input AND gates (one per product term) plus inverters to generate A′, B′, and C′ where required, followed by a 3-input OR gate. The simplified circuit realizes AB + AC + BC with only three 2-input AND gates and a single OR gate, and requires no inverters at all. Both versions were tested with identical input combinations in Logisim, and their outputs matched in every case, confirming that the algebraic and Karnaugh-map reductions are valid. The simplified design is clearly more efficient, using fewer gates, fewer total gate inputs, and eliminating inverters entirely.

### Conclusion
The expression F = A′BC + AB′C + ABC′ + ABC was successfully reduced to F = AB + AC + BC using Boolean algebra and confirmed with a Karnaugh map. Logisim simulation of both the original and simplified circuits produced matching outputs across all input combinations, verifying the correctness of the simplification.

---

## Problem 2: Absorption Law

### Problem Definition
Simplify the Boolean expression F(A, B, C) = A(A + B)(A + B + C) using Boolean algebra and the Karnaugh map, and verify both the original and simplified circuits through logic simulation.

### Objective
To reduce a three-variable product-of-sums-style expression to its simplest form, to confirm this reduction with a Karnaugh map, and to verify in Logisim that the original and simplified circuits are equivalent.

### Algebraic Simplification

```
F(A, B, C) = A(A + B)(A + B + C)
           = (A + AB)(A + B + C)
           = A(A + B + C) + AB(A + B + C)
           = A + AB + AC + AB + AB + ABC
           = A + AB + AC + ABC
           = A(1 + B + C + BC)
           = A
```

### Truth Table

| A | B | C | F = A |
|---|---|---|-------|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

### Karnaugh Map

| A \ BC | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| 0      | 0  | 0  | 0  | 0  |
| 1      | 1  | 1  | 1  | 1  |

All four cells in the A = 1 row are 1, while the entire A = 0 row is 0. These four adjacent cells form a single group spanning the whole row, eliminating both B and C and leaving only F = A, exactly matching the algebraic result.

### Circuit Diagram

<img width="1782" height="463" alt="image" src="https://github.com/user-attachments/assets/a428de3a-fe92-4a76-8e1a-e0d697cbaf3e" />


**Figure 2:** Original circuit (two OR gates realizing A + B and A + B + C, combined with A through an AND gate) and simplified circuit (a direct wire connection representing F = A), simulated in Logisim.

### Discussion
The original circuit builds A + B using one OR gate, extends it to A + B + C with a second OR gate, and ANDs both intermediate results with A itself. Since A is common to every term, all higher-order terms are absorbed and the entire network collapses to the single literal A, so the simplified circuit is nothing more than a direct wire from input A to the output, with no logic gates involved. This is an example of the absorption law A + AB = A applied twice in succession. Testing both circuits in Logisim across all combinations of A, B, and C showed that the output always equals A regardless of B and C, confirming the simplification.

### Conclusion
The expression F = A(A + B)(A + B + C) was shown to reduce to F = A through repeated application of the absorption law, a result confirmed by both the Karnaugh map and Logisim simulation, which demonstrated that B and C have no effect whatsoever on the output.

---

## Problem 3: De Morgan's Theorem

### Problem Definition
Simplify the Boolean expression F(A, B, C) = (A + (BC)′)′(AB + ABC) using Boolean algebra and the Karnaugh map, and verify both the original and simplified circuits through logic simulation.

### Objective
To reduce a mixed AND-OR-complement expression using De Morgan's theorem and Boolean algebra, to confirm the result with a Karnaugh map, and to verify in Logisim that the simplified circuit behaves as a constant.

### Algebraic Simplification

```
F(A, B, C) = (A + (BC)′)′(AB + ABC)
           = A′ · BC · (AB + ABC)      (De Morgan's theorem)
           = A′BC · AB(1 + C)
           = A′BC · AB
           = (AA′) BC B
           = 0
```

### Truth Table

| A | B | C | F = 0 |
|---|---|---|-------|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 |

### Karnaugh Map

| A \ BC | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| 0      | 0  | 0  | 0  | 0  |
| 1      | 0  | 0  | 0  | 0  |

Every cell of the map contains a 0, so there are no 1-cells available for grouping. A Karnaugh map with no populated cells represents the constant function F = 0, confirming the algebraic result.

### Circuit Diagram
<img width="1680" height="520" alt="image" src="https://github.com/user-attachments/assets/84dc6e2d-c52b-40b1-b6dd-fb675b5518e4" />


**Figure 3:** Original circuit realizing (A + (BC)′)′(AB + ABC) using NAND-type and OR/AND stages, and simplified circuit showing the output permanently held at logic 0, simulated in Logisim.

### Discussion
Applying De Morgan's theorem to (A + (BC)′)′ converts it into A′ · BC, after which the second factor AB + ABC simplifies to AB by absorption (AB + ABC = AB(1 + C) = AB). Multiplying A′BC by AB introduces the term A · A′, which is always 0, forcing the entire expression to 0 regardless of the values of A, B, and C. This was confirmed in Logisim by cycling through all eight input combinations on the original circuit and observing that the output never leaves logic 0, exactly as predicted by the all-zero Karnaugh map.

### Conclusion
The expression F = (A + (BC)′)′(AB + ABC) was shown to be identically zero for every input combination. This was verified algebraically, confirmed by an empty Karnaugh map, and validated through Logisim simulation, which produced a constant logic-0 output regardless of A, B, and C.

---

## Problem 4: Two-Variable Reduction

### Problem Definition
Simplify the Boolean expression F(A, B) = (B′(A + B) + (A + B)(A + B′))B′ using Boolean algebra and the Karnaugh map, and verify both the original and simplified circuits through logic simulation.

### Objective
To reduce a two-variable expression built from nested OR and AND terms to its minimal form, to confirm this reduction with a Karnaugh map, and to verify the equivalence of the original and simplified circuits in Logisim.

### Algebraic Simplification

```
F(A, B) = (B′(A + B) + (A + B)(A + B′))B′
        = (AB′ + BB′ + AA + AB′ + AB′ + BB′)B′
        = (A + AB′ + AB′ + AB′)B′
        = A(1 + B′ + B′ + B′) B′
        = AB′
```

### Truth Table

| A | B | F = AB′ |
|---|---|---------|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### Karnaugh Map

| A \ B | 0 | 1 |
|-------|---|---|
| 0     | 0 | 0 |
| 1     | 1 | 0 |

Only a single cell, at A = 1, B = 0, is populated. A lone 1-cell cannot be combined with any neighboring cell, so it is read directly as the product of its coordinate literals, giving F = AB′, which matches the algebraic result.

### Circuit Diagram

<img width="1703" height="469" alt="image" src="https://github.com/user-attachments/assets/861e9dae-7195-4011-9f3b-87e6524237e0" />

**Figure 4:** Original circuit realizing (B′(A + B) + (A + B)(A + B′))B′ using OR, AND, and NOT stages, and simplified circuit reduced to a single AND gate realizing AB′, simulated in Logisim.

### Discussion
Expanding the original expression term by term produces several instances of AB′ along with the terms A, BB′, and AA; since BB′ = 0 and AA = A, and every surviving term is either A or AB′, factoring out the common literal B′ across the whole expression collapses it to the single term AB′. Consequently, the four-gate original network, built from OR, AND, and NOT gates as shown in the Logisim schematic, is functionally equivalent to a single 2-input AND gate with B inverted. Verifying both circuits in Logisim across all four input combinations of A and B confirmed that the output is 1 only when A = 1 and B = 0, matching F = AB′ in every case.

### Conclusion
The expression F = (B′(A + B) + (A + B)(A + B′))B′ was successfully reduced to F = AB′ using Boolean algebra, confirmed with a Karnaugh map, and validated by Logisim simulation, which showed identical outputs for the original and simplified circuits across all input combinations.

---
