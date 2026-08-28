# Computer Engineering - VHDL Digital Systems & Arithmetic Circuits

Repositório de atividades práticas e projetos de Sistemas Digitais em VHDL (Engenharia / Ciência da Computação - UFSC).

---

## 🗂️ Exercícios & Projetos

| Pasta / Exercício | Objetivo | Resultado Principal |
| :--- | :--- | :--- |
| [**`01-troca-sinal-4bits`**](./01-troca-sinal-4bits/) | Inversão de sinal em complemento de 2 ($-B = \overline{B} + 1$). | Implementação estrutural com Full Adders e Half Adders + detecção de overflow. |

---

## 🛠️ Simulação (GHDL)

```bash
cd 01-troca-sinal-4bits
ghdl -a HalfAdder.vhdl FullAdder.vhdl TrocaSinal4Bits.vhdl
```
