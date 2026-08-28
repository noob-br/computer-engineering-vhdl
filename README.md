# Computer Engineering - VHDL Digital Systems & Arithmetic Circuits

Repositório de atividades práticas e projetos de Sistemas Digitais desenvolvidos em VHDL (UFSC).

---

## Exercícios & Projetos

| Pasta | Descrição | Implementação |
| :--- | :--- | :--- |
| [**`01-troca-sinal-4bits`**](./01-troca-sinal-4bits/) | Inversão de sinal em complemento de 2 ($-B = \overline{B} + 1$). | Modelagem estrutural com Full Adders e Half Adders, incluindo detecção de overflow. |

---

## Simulação e Testes

Os códigos utilizam o padrão VHDL-2008 e podem ser analisados com GHDL, ModelSim, Vivado ou Quartus:

```bash
cd 01-troca-sinal-4bits
ghdl -a HalfAdder.vhdl FullAdder.vhdl TrocaSinal4Bits.vhdl
```
