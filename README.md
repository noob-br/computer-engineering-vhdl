# Computer Engineering - VHDL Digital Systems & Arithmetic Circuits

Repositório de atividades práticas e projetos de Sistemas Digitais em VHDL (Engenharia / Ciência da Computação - UFSC).

---

## 🗂️ Exercícios & Projetos

| Pasta / Exercício | Objetivo | Resultado Principal |
| :--- | :--- | :--- |
| [**`01-troca-sinal-4bits`**](./01-troca-sinal-4bits/) | Inversão de sinal em complemento de 2 ($-B = \overline{B} + 1$). | Implementação estrutural com Full Adders e Half Adders + detecção de overflow. |

---

## 🧪 Tabela de Testes & Simulação (Exemplo: Troca de Sinal)

Faixa válida de representação em 4 bits com sinal: **$-8$ até $+7$**.

| Entrada $B$ (Binário) | $B$ (Decimal) | Saída $S = -B$ (Binário) | $S$ (Decimal) | Overflow | Status / Observação |
| :---: | :---: | :---: | :---: | :---: | :--- |
| `0011` | $+3$ | `1101` | $-3$ | `0` | ✅ Válido |
| `0111` | $+7$ | `1001` | $-7$ | `0` | ✅ Válido (limite positivo) |
| `0000` | $0$ | `0000` | $0$ | `0` | ✅ Válido |
| `1101` | $-3$ | `0011` | $+3$ | `0` | ✅ Válido |
| `1000` | $-8$ | `1000` | $-8$ | `1` | ⚠️ **Inválido / Overflow** ($+8$ não cabe em 4 bits) |

---

## 🛠️ Como Simular (GHDL)

```bash
cd 01-troca-sinal-4bits
ghdl -a HalfAdder.vhdl FullAdder.vhdl TrocaSinal4Bits.vhdl
```
