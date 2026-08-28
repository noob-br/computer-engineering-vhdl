# Exercício 1: Circuito "Troca Sinal" de 4 Bits em VHDL

Implementação de um circuito aritmético de troca de sinal em complemento de dois ($S = -B$) para palavras de 4 bits com flag de detecção de overflow.

---

## 🎯 Objetivo

Implementar duas arquiteturas estruturais para a mesma entidade `TrocaSinal4Bits`:
1. **`usingFAs`**: Correção e uso de **Full Adders** (Somadores Completos).
2. **`usingHAs`**: Implementação estrutural utilizando apenas **Half Adders** (Meio Somadores).

---

## ⚙️ Regras de Implementação

- **Equação Aritmética:** $-B = \overline{B} + 1$
- Usar **Full Adder** apenas em `usingFAs` e **Half Adder** apenas em `usingHAs`.
- Instanciação direta por entidade (`ENTITY work.Component(arch)`), sem declaração de componentes.
- Associação puramente nominal no `PORT MAP` (`porta => sinal`).
- Detecção de overflow via hardware: $\text{overflow} = C_{in\_MSB} \oplus C_{out\_MSB} = c(3) \oplus c(4)$.

---

## 📂 Arquivos

- [`TrocaSinal4Bits.vhdl`](./TrocaSinal4Bits.vhdl): Entidade principal e as duas arquiteturas (`usingFAs` e `usingHAs`).
- [`FullAdder.vhdl`](./FullAdder.vhdl): Componente Full Adder de 1 bit.
- [`HalfAdder.vhdl`](./HalfAdder.vhdl): Componente Half Adder de 1 bit.
- [`resumo_aprendizado.md`](./resumo_aprendizado.md): Anotações detalhadas de dúvidas conceituais, sintaxe e conclusões.
