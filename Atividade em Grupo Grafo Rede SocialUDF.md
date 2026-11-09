# Caderno do Estudante

# Projeto ConectaUDF: redes sociais com grafos

**Disciplina:** Algoritmos / Matemática Discreta / Ciência de Dados

## 1\. O desafio

Você faz parte da equipe que analisa a rede social fictícia **ConectaUDF**. Sua missão é representar as amizades em um grafo, realizar cálculos e usar Python para interpretar a estrutura da rede.

## 2\. Conceitos essenciais

- **Vértice (ou nó):** representa um usuário.  
- **Aresta:** representa uma amizade entre dois usuários.  
- **Grau:** quantidade de conexões diretas de um usuário.  
- **Caminho:** sequência de usuários em que cada par consecutivo está conectado.  
- **Densidade:** proporção entre as amizades existentes e todas as amizades possíveis.

Neste projeto, a amizade é recíproca. Portanto, usamos um **grafo não direcionado**.

## 3\. Conheça os usuários

| Código | Usuário |
| :---- | :---- |
| A | Marcos |
| B | Davi |
| C | Webster |
| D | Ênio |
| E | Arthur |

As amizades são:

1. Davi — Webster  
2. Davi — Ênio  
3. Davi — Marcos  
4. Davi — Arthur  
5. Arthur — Lucas  
6. Gabriel — Julia  
7. Joana — Julia  
8. Gabriel — Marcos

## 4\. Passo a passo: desenhe o grafo

1. Desenhe seis círculos, um para cada usuário.  
2. Escreva o nome de cada pessoa dentro do círculo.  
3. Para cada amizade da lista, desenhe uma linha entre os dois usuários.  
4. Não desenhe duas linhas para a mesma amizade.  
5. Confira se todas as oito amizades aparecem.

![][image1]

**Espaço para o seu desenho:** faça o grafo no caderno ou em uma ferramenta de desenho.

## 5\. Passo a passo: calcule o grau

Conte quantas linhas chegam a cada círculo. Registre o resultado.

| Usuário | Amigos diretos | Grau |
| :---- | :---- | ----: |
| Davi | Ênio, Webster, Marcos, Arthur | 4 |
| Webster | Davi, Marcos, Ênio | 3 |
| Marcos | Davi, Webster,  | 2 |
| Ênio | Davi, Webster | 2 |
| Arthur | Lucas, Davi | 1 |

**Pergunta 1:** quem tem mais conexões diretas?  
Resposta: Davi

## 6\. Passo a passo: calcule o número de amizades

Some todos os graus. Como cada amizade conecta dois usuários, cada aresta é contada duas vezes.

**Fórmula:**  
`Número de arestas =  soma dos graus ÷ 2`

1. Soma dos graus: 12  
2. Divida por 2: 12 ÷ 2 \= 6  
3. Quantas amizades existem no grafo? 6

## 7\. Passo a passo: calcule a densidade

A densidade compara as amizades existentes com o total de amizades possíveis.

Para um grafo simples não direcionado:

`D = 2 × E / (V × (V − 1))`

Em que:

- `D` \= densidade;  
- `E` \= número de arestas;  
- `V` \= número de vértices.

Substitua os valores: `D = 2 × 6 / (5 × (5 − 1))`

Resultado decimal: 0,6  
Resultado percentual: 60%

**Interprete:** a rede tem poucas ou muitas das conexões possíveis? Explique com suas palavras. A rede possui poucas amizades comparado ao total de amizades possíveis, apenas 30% da rede é conectada

---

## 8\. Passo a passo: Represente o grafo em Python

A lista de adjacência registra, para cada usuário, os nomes de seus amigos. Digite o código em Python (por exemplo, no Google Colab ou em outro ambiente disponível).

```py
rede = {
"Davi": ["Marcos", "Webster", "Arthur", "Ênio"],
"Marcos": ["Webster", "Davi"],
"Webster": ["Marcos", "Davi", "Ênio"],
"Arthur": ["Davi"],
"Ênio": ["Davi", "Webster"]
}
n = len(rede)
soma_graus = sum(len(a) for a in rede.values())
E = soma_graus // 2
D = 2 * E / (n * (n - 1))
print(f"Total de usuários: {n}")
print(f"Total de amizades: {E}")
print(f"Densidade: {D:.2%}")
graus = {pessoa: len(amigos) for pessoa, amigos in rede.items()}
ranking = sorted(graus.items(), key=lambda item: item[1], reverse=True)
print()
print(f"{'Pessoa':<10} {'Grau':<5} Amigos")


```

### Entenda o código

1. `rede` guarda os usuários e suas listas de amigos.  
2. `len(rede)` conta os usuários.  
3. `len(amigos)` calcula o grau de cada usuário.  
4. `sum(...)` soma os graus.  
5. `// 2` divide a soma por dois para contar cada amizade uma única vez.  
6. A fórmula final calcula a densidade.

## 9\. Passo a passo: encontre um caminho

Encontre um caminho de Davi até Julia. Cada passagem por uma linha corresponde a uma aresta.

Exemplo de registro: `Marcos → Davi → Arthur`

- Quantas arestas há no caminho? 2  
- Você encontrou outro caminho com a mesma quantidade de arestas? Qual?  
  Sim, Davi → Webster → Arthur

## 10\. Desafio em grupo

Amplie a rede social:

1. Adicione pelo menos quatro usuários fictícios.   
   **Nomes: Lucas, Joana, Julia e Gabriel**  
2. Crie no mínimo cinco novas amizades.

![][image2]

3. Atualize a lista de adjacência no Python.  
4. Recalcule os graus, o total de arestas e a densidade.

**Densidade**:  
**D** \= 2E / \[V × (V − 1)\]  
**D** \= 2 \* 11 / \[9 \* (9 – 1)\]  
**D** \= 22 / 9 \* (9 – 1\)  
**D** \= 22 / 9 \* 8

**D** \= 22 / 72  
**D** **\~ 0,305 \~ 30,56%**  
E \= **11** amizades  
V \= **9** usuários

5. Compare a densidade antes e depois da ampliação.

Antes: **5** usuários e **6** amizades.  
Depois: **9** usuários e **11** amizades.  
Antes: **D \= 0,6 \= 60%.**  
Depois: **D \~ 0,305 \~ 30,56%.**

6. Identifique os usuários com mais conexões.  
   **Davi, Marcos e Webster**  
7. Explique como a rede poderia recomendar uma nova amizade.  
   **Podemos recomendar pessoas através dos amigos em**  
   **comum. Exemplo, Marcos e Arthur tem Davi como amigo**  
   **em comum, então Marcos ou Arthur poderiam receber**  
   **sugestões para ambos.**  
   

Código

```py
rede = {
"Davi": ["Marcos", "Webster", "Arthur", "Ênio"],
"Marcos": ["Webster", "Davi", "Gabriel"],
"Webster": ["Marcos", "Davi", "Ênio"],
"Arthur": ["Davi", "Lucas"],
"Ênio": ["Davi", "Webster"],
"Gabriel": ["Julia", "Marcos"],
"Julia": ["Gabriel", "Joana"],
"Joana": ["Julia", "Lucas"],
"Lucas": ["Joana", "Arthur"],
}
n = len(rede)
soma_graus = sum(len(a) for a in rede.values())
E = soma_graus // 2
D = 2 * E / (n * (n - 1))

print(f"Total de usuários: {n}")
print(f"Total de amizades: {E}")
print(f"Densidade: {D:.2%}")

graus = {pessoa: len(amigos) for pessoa, amigos in rede.items()}
ranking = sorted(graus.items(), key=lambda item: item[1], reverse=True)

print()
print(f"{'Pessoa':<10} {'Grau':<5} Amigos")
for pessoa, grau in ranking:
print(f"{pessoa:<10} {grau:<5} {', '.join(rede[pessoa])}")

```

## 11\. Entrega

Entregue:

- desenho do grafo;  
- tabela com os graus;  
- cálculos de arestas e densidade;  
- código Python executável;  
- respostas às perguntas e breve conclusão.

## 12\. Pergunta de reflexão

Duas pessoas ainda não são amigas, mas têm três amigos em comum. Como essa informação poderia ser usada para sugerir uma nova conexão? Quais cuidados de privacidade devem ser considerados ao analisar redes sociais?  
**Podemos recomendar pessoas através dos amigos em**  
**comum. Solicitar autorização antes de compartilhar informações.**  
**Permitir que os usuários controlem quem pode visualizar**  
**suas amizades.** 

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,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>
