# Trabalho Semanal (14-Maio): Aprendizado Indutivo em Programação em Lógica

## How To

1. (Linux) Instalar swi-prolog com os comandos (caso ainda não tenha):

```bash
sudo apt-add-repository ppa:swi-prolog/devel
sudo apt-get update
sudo apt-get install swi-prolog
```

2. Mover-se para o diretório do trabalho e fazer o lauch do swi-prolog

```bash
cd trabalho_semanal_14052026
swipl
```

3. Para executar o exercício 21.1:

```bash
?- [trab_sem_02_exc_21_1].

?- induce(H).
```

4. Para executar o exercício 21.2:

```bash
?- [trab_sem_02_exc_21_2].

?- induce(H).
```

---

## Resultados

### 21.1 - Experimentos com conjuntos de exemplos de `has_daughter` modificados

- Provendo exemplos apenas de pais (e não de mães) de filhas, a hipótese resultante agora define o gênero do pai, em vez do da criança.

```
?- induce(H).
MaxD= 0
MaxD= 1
MaxD= 2
MaxD= 3
MaxD= 4
H = [[has_daughter(_A), parent(_A, _B), male(_A)]/[_B, _A]]
```

### 21.2 - Quantidade de etapas de refinamento para o código com `predecessor`

Para chegar à hipótese alvo a partir do estado inicial, o programa realiza **8 passos de refinamento** no total ($3 + 5 = 8$). O mecanismo de busca por aprofundamento iterativo encontrará a solução correta quando atingir a profundidade **`MaxD= 8`**.

* **Cláusula 1 (Caso Base): 3 passos**
* 1 adição de literal: `parent(X3, Y3)`
* 2 unificações de variáveis: vincular as variáveis novas às originais para formar `predecessor(X, Y) :- parent(X, Y).`


* **Cláusula 2 (Caso Recursivo): 5 passos**
* 2 adições de literais: `parent(X4, Y4)` e `predecessor(X5, Y5)`
* 3 unificações de variáveis: vincular as variáveis para criar a conexão intermediária (o "Z") e formar `predecessor(X, Y) :- parent(X, Z), predecessor(Z, Y).`
