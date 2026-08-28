# Relatório de Aprendizagem & Dificuldades: TrocaSinal4Bits (VHDL)

Este documento sintetiza os principais pontos de dúvida, dificuldades encontradas e as conclusões consolidadas durante o desenvolvimento do circuito de negação em complemento de dois (`TrocaSinal4Bits`) com Half Adders.

---

## 📌 Dificuldades Apresentadas Durante a Atividade

### 1. Escopo e Independência das Arquiteturas em VHDL
* **Dúvida:** Existia a dúvida se a atribuição `b_inv <= not b;` feita na primeira arquitetura (`usingFAs`) valia automaticamente para a segunda (`usingHAs`), ou se era necessário reatribuir.
* **Esclarecimento:** Cada arquitetura em VHDL é um bloco independente e concorrente. A declaração do sinal (`SIGNAL b_inv ...`) no cabeçalho da arquitetura apenas cria o "fio", sendo estritamente necessário atribuir seu valor (`b_inv <= NOT b;`) dentro do `BEGIN` de cada arquitetura onde ele for utilizado.

---

### 2. Sintaxe e Semântica do `PORT MAP`
* **Dúvidas:**
  * De onde vinha a porta de saída `s => s(0)`?
  * O sentido do operador `=>`: parecia que o sinal da direita estava sendo atribuído ao da esquerda (`a <= b_inv(0)` vs `a => b_inv(0)`).
  * Pontuação: uso de `=` em vez de `=>`, fechamento de parênteses `);` e separação por vírgulas.
* **Esclarecimento:**
  * No `PORT MAP`, o operador `=>` significa **conexão/associação de pinos**, e não atribuição procedural.
  * **Lado esquerdo:** Nome do pino da entidade instanciada (`HalfAdder`: `a`, `b`, `s`, `cout`).
  * **Lado direito:** Sinal ou porta do circuito atual (`b_inv(0)`, `'1'`, `s(0)`, `c(1)`).
  * `s(0)` da direita é o pino da entidade pai (`TrocaSinal4Bits`), que expõe o bit menos significativo do resultado final `-b`.

---

### 3. Compreensão e Detecção de Overflow em Complemento de Dois
* **Dúvidas:**
  * Por que usar $c(3) \oplus c(4)$ para calcular o `overflow`?
  * Por que somar `1000 + 1000` gera overflow (`c3 xor c4 = 1`), mas somar `1100 + 1100` não gera overflow (`c3 xor c4 = 0`) se ambas são somas de negativos?
* **Esclarecimento:**
  * Em representação de 4 bits com sinal (faixa $[-8, +7]$):
    * `1000` é $-8$. A soma $(-8) + (-8) = -16$ extrapola a capacidade $\implies$ **Overflow** ($c_3 = 0, c_4 = 1 \implies 0 \oplus 1 = 1$).
    * `1100` é $-4$. A soma $(-4) + (-4) = -8$ (`1000`), que cabe perfeitamente na faixa $\implies$ **Sem Overflow** ($c_3 = 1, c_4 = 1 \implies 1 \oplus 1 = 0$).
  * A regra geral para somadores com sinal é: $\text{overflow} = C_{in\_MSB} \oplus C_{out\_MSB}$.

---

## 🎯 Conclusão do Exercício

1. **Aritmética de Troca de Sinal (Complemento de Dois):**
   * A operação $-B = \overline{B} + 1$ foi realizada em hardware sem a necessidade de somadores completos (Full Adders de 3 entradas) no primeiro estágio, bastando um **Half Adder** somando $\overline{b(0)}$ com a constante `'1'`.

2. **Propagação Modular de Carry (Ripple Carry):**
   * O carry gerado no estágio $i$ alimenta a entrada do estágio subsequente $i+1$, dispensando somadores completos porque sempre somamos apenas 2 termos em cada estágio: o bit invertido correspondente $\overline{b(i)}$ e o carry anterior $c(i)$.

3. **Arquitetura Estrutural Limpa:**
   * O circuito final utilizou 4 instâncias de `HalfAdder`, manipulando vetores de sinais internos (`b_inv` e `c`) e gerando corretamente o sinal de status `overflow`.
