# Exercício 1: Circuito "Troca Sinal" de 4 Bits em VHDL

Implementação de um circuito aritmético de troca de sinal em complemento de dois ($S = -B$) para palavras de 4 bits com flag de detecção de overflow.

---

## Objetivo

Implementar duas arquiteturas estruturais para a entidade `TrocaSinal4Bits`:
1. **`usingFAs`**: Implementação utilizando **Full Adders** (Somadores Completos).
2. **`usingHAs`**: Implementação estrutural utilizando apenas **Half Adders** (Meio Somadores).

---

## Regras de Projeto

- **Operação aritmética:** $-B = \overline{B} + 1$ (inversão bit a bit seguida de soma com 1).
- Instanciação direta por entidade (`ENTITY work.Component(arch)`), sem declaração de `COMPONENT`.
- Associação nominal explícita no `PORT MAP` (`porta => sinal`).
- Detecção de overflow em complemento de dois: $\text{overflow} = C_{in\_MSB} \oplus C_{out\_MSB} = c(3) \oplus c(4)$.

---

## Casos de Teste (Faixa com sinal: -8 a +7)

| Entrada $B$ (Binário) | $B$ (Decimal) | Saída $S = -B$ (Binário) | $S$ (Decimal) | Overflow | Observação |
| :---: | :---: | :---: | :---: | :---: | :--- |
| `0011` | $+3$ | `1101` | $-3$ | `0` | Operação válida |
| `0111` | $+7$ | `1001` | $-7$ | `0` | Operação válida (limite superior) |
| `0000` | $0$ | `0000` | $0$ | `0` | Operação válida |
| `1101` | $-3$ | `0011` | $+3$ | `0` | Operação válida |
| `1000` | $-8$ | `1000` | $-8$ | `1` | **Overflow**: $+8$ extrapola a faixa de 4 bits |

---

## Arquivos do Módulo

- [`TrocaSinal4Bits.vhdl`](./TrocaSinal4Bits.vhdl): Entidade principal e arquiteturas estruturais (`usingFAs` e `usingHAs`).
- [`FullAdder.vhdl`](./FullAdder.vhdl): Componente Somador Completo de 1 bit.
- [`HalfAdder.vhdl`](./HalfAdder.vhdl): Componente Meio Somador de 1 bit.
- [`resumo_aprendizado.md`](./resumo_aprendizado.md): Anotações de síntese conceitual e dúvidas da implementação.
