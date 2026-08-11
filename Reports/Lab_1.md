# Digital Logic Gates & Circuits

A collection of fundamental digital logic circuits implemented and simulated to demonstrate core concepts of digital electronics — including universal gate derivations (NAND/NOR), a Full Adder, and an 8-Bit BCD circuit.


## All Fundamental Logic Gates using NOR Gate

The **NOR gate** is a universal gate, meaning any other logic gate (NOT, AND, OR, NAND, XOR, XNOR) can be constructed using only NOR gates. This circuit demonstrates how each fundamental gate is derived using combinations of NOR gates alone.

### Description

- **NOT Gate:** Formed by connecting both inputs of a NOR gate together.
- **OR Gate:** Formed by inverting the output of a NOR gate.
- **AND Gate:** Formed by inverting the inputs before feeding them into a NOR gate.
- **NAND Gate:** Formed by inverting the output of the AND (NOR-derived) construction.
- **XOR Gate:** Formed using a combination of multiple NOR gates.
- **XNOR Gate:** Formed by inverting the output of the XOR (NOR-derived) construction.

### Truth Table (Basic NOR Gate)

| A | B | Output (A NOR B) |
|---|---|-------------------|
| 0 | 0 | 1                 |
| 0 | 1 | 0                 |
| 1 | 0 | 0                 |
| 1 | 1 | 0                 |

### Circuit Diagram

<img width="648" height="634" alt="All Fundamental Logic Gates using NOR Gate" src="https://github.com/user-attachments/assets/ba85dd0f-930a-41ad-b910-965fd08850c5" />

---

## All Fundamental Logic Gates using NAND Gate

The **NAND gate** is also a universal gate. Similar to the NOR-based approach, every fundamental logic gate can be constructed purely using NAND gates.

### Description

- **NOT Gate:** Formed by connecting both inputs of a NAND gate together.
- **AND Gate:** Formed by inverting the output of a NAND gate.
- **OR Gate:** Formed by inverting the inputs before feeding them into a NAND gate.
- **NOR Gate:** Formed by inverting the output of the OR (NAND-derived) construction.
- **XOR Gate:** Formed using a combination of multiple NAND gates.
- **XNOR Gate:** Formed by inverting the output of the XOR (NAND-derived) construction.

### Truth Table (Basic NAND Gate)

| A | B | Output (A NAND B) |
|---|---|--------------------|
| 0 | 0 | 1                  |
| 0 | 1 | 1                  |
| 1 | 0 | 1                  |
| 1 | 1 | 0                  |

### Circuit Diagram

<img width="687" height="585" alt="All Fundamental Logic Gates using NAND Gate" src="https://github.com/user-attachments/assets/beae28b2-08e8-4542-a31d-14cdd845c0cd" />

---

## Full Adder

A **Full Adder** is a combinational circuit that performs the addition of three binary bits: two significant bits (A and B) and a carry-in bit (Cin) from a previous addition stage. It produces two outputs: the **Sum** and the **Carry-out (Cout)**.

### Description

- Takes **three inputs**: A, B, and Cin (carry-in).
- Produces **two outputs**: Sum and Cout (carry-out).
- Built using two Half Adders and an OR gate, or directly using AND, OR, and XOR gates.
- Used in multi-bit binary adders by cascading multiple Full Adder circuits together.

### Truth Table

| A | B | Cin | Sum | Cout |
|---|---|-----|-----|------|
| 0 | 0 | 0   | 0   | 0    |
| 0 | 0 | 1   | 1   | 0    |
| 0 | 1 | 0   | 1   | 0    |
| 0 | 1 | 1   | 0   | 1    |
| 1 | 0 | 0   | 1   | 0    |
| 1 | 0 | 1   | 0   | 1    |
| 1 | 1 | 0   | 0   | 1    |
| 1 | 1 | 1   | 1   | 1    |

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
