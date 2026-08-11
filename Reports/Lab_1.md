# Digital Logic Gates & Circuits

A collection of fundamental digital logic circuits implemented and simulated to demonstrate core concepts of digital electronics — including universal gate derivations (NAND/NOR), a Full Adder, and an 8-Bit BCD circuit.

---

## All Fundamental Logic Gates using NOR Gate

The **NOR gate** is a universal gate, meaning any other logic gate can be constructed using only NOR gates. This circuit demonstrates three separate derivations — **NOT**, **OR**, and **AND** — built entirely from NOR gates.

### Description

- **NOT Gate:** Formed by connecting both inputs of a single NOR gate together, so it acts as an inverter.
- **OR Gate:** Formed by feeding two NOR gates in cascade — the first NOR gate combines A and B, and the second NOR gate (used as a NOT) inverts that result back to a plain OR.
- **AND Gate:** Formed using De Morgan's construction — each input is first inverted by its own NOR-based NOT gate, and the inverted signals are then combined by a final NOR gate to produce the AND output.

### Truth Table 1 — NOT Gate (from NOR)

| A | Output (NOT A) |
|---|-----------------|
| 0 | 1               |
| 1 | 0               |

### Truth Table 2 — OR Gate (from NOR)

| A | B | Output (A OR B) |
|---|---|------------------|
| 0 | 0 | 0                |
| 0 | 1 | 1                |
| 1 | 0 | 1                |
| 1 | 1 | 1                |

### Truth Table 3 — AND Gate (from NOR)

| A | B | Output (A AND B) |
|---|---|-------------------|
| 0 | 0 | 0                 |
| 0 | 1 | 0                 |
| 1 | 0 | 0                 |
| 1 | 1 | 1                 |

### Circuit Diagram

<img width="648" height="634" alt="All Fundamental Logic Gates using NOR Gate" src="https://github.com/user-attachments/assets/ba85dd0f-930a-41ad-b910-965fd08850c5" />

---

## All Fundamental Logic Gates using NAND Gate

The **NAND gate** is also a universal gate. Similar to the NOR-based approach, this circuit demonstrates three separate derivations — **AND**, **OR**, and **NOT** — built entirely from NAND gates.

### Description

- **AND Gate:** Formed by cascading two NAND gates — the first NAND combines A and B, and the second NAND (used as a NOT) inverts that result back to a plain AND.
- **OR Gate:** Formed using De Morgan's construction — each input is first inverted by its own NAND-based NOT gate, and the inverted signals are then combined by a final NAND gate to produce the OR output.
- **NOT Gate:** Formed by connecting both inputs of a single NAND gate together, so it acts as an inverter.

### Truth Table 1 — AND Gate (from NAND)

| A | B | Output (A AND B) |
|---|---|-------------------|
| 0 | 0 | 0                 |
| 0 | 1 | 0                 |
| 1 | 0 | 0                 |
| 1 | 1 | 1                 |

### Truth Table 2 — OR Gate (from NAND)

| A | B | Output (A OR B) |
|---|---|------------------|
| 0 | 0 | 0                |
| 0 | 1 | 1                |
| 1 | 0 | 1                |
| 1 | 1 | 1                |

### Truth Table 3 — NOT Gate (from NAND)

| A | Output (NOT A) |
|---|-----------------|
| 0 | 1               |
| 1 | 0               |

### Circuit Diagram

<img width="687" height="585" alt="All Fundamental Logic Gates using NAND Gate" src="https://github.com/user-attachments/assets/beae28b2-08e8-4542-a31d-14cdd845c0cd" />

---

## Full Adder

A **Full Adder** is a combinational circuit that performs the addition of three binary bits: two significant bits (A and B) and a carry-in bit (Cin) from a previous addition stage. It produces two outputs: the **Sum** and the **Carry-out (Cout)**. The diagram shows the Full Adder implemented in two ways: using a **built-in Adder component** (with Cin/Cout), and using **two cascaded Half Adders** built from XOR/AND/OR gates.

### Description

- **Built-in Full Adder block:** Takes A, B, and Cin as inputs, and directly outputs Sum and Cout.
- **Half Adder 1:** Takes inputs A and B, and produces an intermediate Sum (A XOR B) and an intermediate Carry (A AND B).
- **Half Adder 2 + OR stage:** Takes the intermediate Sum from Half Adder 1 along with Cin to produce the final Sum, while the two intermediate carries are combined with an OR gate to produce the final Cout.

### Truth Table 1 — Half Adder 1 (A, B)

| A | B | Sum1 (A XOR B) | Carry1 (A AND B) |
|---|---|----------------|-------------------|
| 0 | 0 | 0              | 0                 |
| 0 | 1 | 1              | 0                 |
| 1 | 0 | 1              | 0                 |
| 1 | 1 | 0              | 1                 |

### Truth Table 2 — Half Adder 2 (Sum1, Cin)

| Sum1 | Cin | Sum (Sum1 XOR Cin) | Carry2 (Sum1 AND Cin) |
|------|-----|---------------------|-------------------------|
| 0    | 0   | 0                   | 0                        |
| 0    | 1   | 1                   | 0                        |
| 1    | 0   | 1                   | 0                        |
| 1    | 1   | 0                   | 1                        |

### Truth Table 3 — Final Full Adder (A, B, Cin)

| A | B | Cin | Sum | Cout (Carry1 OR Carry2) |
|---|---|-----|-----|--------------------------|
| 0 | 0 | 0   | 0   | 0                        |
| 0 | 0 | 1   | 1   | 0                        |
| 0 | 1 | 0   | 1   | 0                        |
| 0 | 1 | 1   | 0   | 1                        |
| 1 | 0 | 0   | 1   | 0                        |
| 1 | 0 | 1   | 0   | 1                        |
| 1 | 1 | 0   | 0   | 1                        |
| 1 | 1 | 1   | 1   | 1                        |

### Circuit Diagram

<img width="830" height="595" alt="Full Adder" src="https://github.com/user-attachments/assets/bd99b739-80c1-47d9-b1dc-22eb20345c56" />

---

## 8-Bit Binary to BCD Converter

This circuit converts an **8-bit binary input** into its equivalent **BCD (Binary Coded Decimal)** representation and displays it on **three 7-segment displays** (Hundreds, Tens, and Units place).

### Description

- Takes an **8-bit binary number** as input (range: 0–255).
- Converts the binary value into **three BCD digits**: Hundreds (100s), Tens (10s), and Units (1s).
- Each BCD digit drives its own **7-segment display**, showing the decimal equivalent of the binary input.
- Commonly implemented using the **Double Dabble (Shift-and-Add-3) algorithm** to convert binary to BCD.
- Useful in digital systems where binary data needs to be shown in human-readable decimal form, such as counters, digital clocks, and measurement displays.

### Truth Table (Sample Binary to BCD Conversions)

| Binary Input | Decimal | Hundreds | Tens | Units |
|--------------|---------|----------|------|-------|
| 00000000     | 0       | 0        | 0    | 0     |
| 00001001     | 9       | 0        | 0    | 9     |
| 00011001     | 25      | 0        | 2    | 5     |
| 01100100     | 100     | 1        | 0    | 0     |
| 11111111     | 255     | 2        | 5    | 5     |

### Circuit Diagram

<img width="807" height="487" alt="8-Bit Binary to BCD Converter" src="https://github.com/user-attachments/assets/68133c12-d8b9-40be-98ef-8434362f18dc" />

---

## Tools Used

- Logic circuit simulation software (Logisim)

## 📄 License

This project is open source and available for educational use.
