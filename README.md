# Computer Engineering - VHDL Digital Systems & Arithmetic Circuits

Repository dedicated to digital logic design, arithmetic circuits, and digital systems modeling using VHDL. Developed as part of coursework and laboratory activities at UFSC.

---

## 📌 Contents

| File | Description |
| :--- | :--- |
| [`HalfAdder.vhdl`](./HalfAdder.vhdl) | 1-bit Half Adder implementation (practical XOR/AND and theoretical CMOS NAND implementations). |
| [`FullAdder.vhdl`](./FullAdder.vhdl) | 1-bit Full Adder with carry-in and carry-out generation. |
| [`TrocaSinal4Bits.vhdl`](./TrocaSinal4Bits.vhdl) | 4-bit Two's Complement Negation unit ($-B = \overline{B} + 1$) implemented with structural architectures using both Full Adders (`usingFAs`) and Half Adders (`usingHAs`), including overflow detection. |

---

## ⚡ Key Concepts Demonstrated

- **Structural VHDL Modeling**: Instantiation of subcomponents (`ENTITY work.HalfAdder`, `ENTITY work.FullAdder`) and hierarchical port mapping.
- **Two's Complement Arithmetic**: Negating numbers via bitwise inversion ($NOT$) followed by incrementing ($+1$).
- **Ripple Carry Propagation**: Carry chaining through modular adders.
- **Overflow Detection**: Hardware condition check ($C_{in\_MSB} \oplus C_{out\_MSB}$) for signed 4-bit range ($[-8, +7]$).

---

## 🛠️ Requirements & Simulation

- Any standard IEEE VHDL-2008 compliant simulator (GHDL, ModelSim, Vivado, Quartus).

```bash
# Example simulation with GHDL
ghdl -a HalfAdder.vhdl FullAdder.vhdl TrocaSinal4Bits.vhdl
```
