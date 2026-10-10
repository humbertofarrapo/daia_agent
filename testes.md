# Atividade 3 — Testes e Validação do Agente MovieBack

## 1. Objetivo dos testes

Os testes foram realizados com o objetivo de verificar o comportamento do agente MovieBack de acordo com as regras e características definidas na Atividade 2. Foram avaliados diferentes tipos de solicitações, considerando critérios de recomendação, múltiplos critérios, solicitações vagas, filmes não disponíveis na base, perguntas fora do domínio, utilização do contexto da conversa e limite de recomendações.

Os testes foram executados no fluxo desenvolvido no n8n, observando-se as respostas apresentadas pelo agente em cada situação.

## 2. Casos de teste

### CT01 — Solicitação por gênero

**Objetivo:** Verificar se o agente consegue realizar recomendações a partir de um único critério.

**Entrada do usuário:**

> Me recomende filmes de ficção científica.

**Resultado obtido:**

* Interestelar
* Blade Runner 2049
* Mad Max: Estrada da Fúria

**Critério de sucesso:** Recomendar filmes do gênero solicitado e respeitar o limite de até 3 filmes.

**Classificação:** ✅ **Atendido**

**Análise:** O agente identificou corretamente o gênero solicitado e apresentou três filmes compatíveis com o critério.

---

### CT02 — Solicitação com múltiplos critérios

**Objetivo:** Verificar se o agente considera simultaneamente gênero e ano de lançamento.

**Entrada do usuário:**

> Quero um filme de ficção científica lançado depois de 2015.

**Resultado obtido:**

* Blade Runner 2049 (2017)
* O Silêncio do Lago (2018)

**Critério de sucesso:** Recomendar somente filmes de ficção científica lançados após 2015.

**Classificação:** ✅ **Atendido**

**Análise:** Os dois filmes apresentados atendem simultaneamente aos critérios de gênero e ano. O agente não adicionou um terceiro filme que não atendesse às condições estabelecidas.

---

### CT03 — Solicitação vaga

**Objetivo:** Verificar o comportamento do agente diante de uma solicitação sem informações suficientes para uma recomendação específica.

**Entrada do usuário:**

> Me recomenda um filme?

**Resultado obtido:** O agente solicitou informações adicionais sobre a preferência do usuário para realizar uma recomendação mais adequada.

**Critério de sucesso:** Solicitar uma informação adicional de forma objetiva quando não houver critérios suficientes para uma recomendação relevante.

**Classificação:** ✅ **Atendido**

**Análise:** O agente identificou que a solicitação era vaga e solicitou uma preferência antes de realizar a recomendação.

---

### CT04 — Filme não disponível na base

**Objetivo:** Verificar se o agente evita inventar informações sobre filmes que não estão disponíveis na base de conhecimento.

**Entrada do usuário:**

> Quais são as informações sobre o filme Titanic 2?

**Resultado obtido:** O agente informou que não havia informações sobre o filme na base de conhecimento.

**Critério de sucesso:** Não inventar informações e informar a indisponibilidade do filme na base.

**Classificação:** ✅ **Atendido**

**Análise:** O agente respeitou a base de conhecimento como fonte oficial e não apresentou informações não disponíveis.

---

### CT05 — Solicitação fora do domínio

**Objetivo:** Verificar se o agente reconhece solicitações que não estão relacionadas ao seu domínio.

**Entrada do usuário:**

> Como faço para declarar meu imposto de renda?

**Resultado obtido:** O agente informou que seu domínio está relacionado a filmes e recomendações cinematográficas.

**Critério de sucesso:** Não responder à solicitação fora do domínio como se possuísse essa função.

**Classificação:** ✅ **Atendido**

**Análise:** O agente identificou corretamente que a solicitação não estava relacionada ao seu domínio de atuação.

---

### CT06 — Utilização do contexto da conversa

**Objetivo:** Verificar se o agente consegue utilizar uma preferência informada anteriormente na conversa.

**Primeira entrada do usuário:**

> Eu gosto de filmes de ficção científica sobre viagem no tempo.

**Resultado obtido:**

* De Volta para o Futuro (1985)
* Interestelar (2014)
* A Origem (2010)

**Segunda entrada do usuário:**

> Pode me recomendar um?

**Resultado obtido:**

* De Volta para o Futuro (1985)

**Critério de sucesso:** Utilizar a preferência apresentada anteriormente para interpretar uma nova solicitação curta.

**Classificação:** ✅ **Atendido**

**Análise:** O agente utilizou o contexto da conversa para compreender a nova solicitação e realizou uma recomendação relacionada à preferência anteriormente informada.

---

### CT07 — Limite de recomendações

**Objetivo:** Verificar se o agente respeita o limite máximo de três recomendações.

**Entrada do usuário:**

> Me indique 10 filmes de ficção científica.

**Resultado obtido:**

* Interestelar
* Blade Runner 2049
* O Grande Truque

**Critério de sucesso:** Apresentar no máximo três filmes, mesmo quando o usuário solicitar uma quantidade superior.

**Classificação:** ✅ **Atendido**

**Análise:** O agente apresentou três recomendações, respeitando o limite estabelecido no comportamento do sistema.

## 3. Resumo dos resultados

| Caso | Situação avaliada            | Resultado |
| ---- | ---------------------------- | --------- |
| CT01 | Solicitação por gênero       | ✅ Atendido  |
| CT02 | Múltiplos critérios          | ✅ Atendido  |
| CT03 | Solicitação vaga             | ✅ Atendido  |
| CT04 | Filme não disponível na base | ✅ Atendido  |
| CT05 | Solicitação fora do domínio  | ✅ Atendido  |
| CT06 | Utilização do contexto       | ✅ Atendido  |
| CT07 | Limite de recomendações      | ✅ Atendido  |

**Total:** 7 casos atendidos, 0 parcialmente atendidos e 0 não atendidos.

## 4. Análise dos resultados

Os testes realizados demonstraram que o comportamento do MovieBack está alinhado às regras definidas para o agente. Foram verificadas situações envolvendo diferentes formas de interação, desde solicitações simples de recomendação até situações que exigem interpretação de critérios, utilização do contexto e aplicação de restrições.

O CT01 demonstrou o funcionamento da recomendação a partir de um gênero específico. O CT02 avaliou a aplicação simultânea de diferentes critérios. O CT03 verificou o comportamento diante de uma solicitação vaga, enquanto o CT04 avaliou a restrição relacionada à utilização exclusiva da base de conhecimento.

O CT05 verificou a delimitação do domínio de atuação do agente. Já o CT06 avaliou a utilização do histórico da conversa para manter uma preferência anteriormente informada. Por fim, o CT07 verificou o cumprimento do limite máximo de recomendações.

Dessa forma, os resultados obtidos indicam que as principais regras definidas para o funcionamento do agente foram respeitadas durante os testes realizados.

## 5. Melhorias identificadas

Apesar dos resultados satisfatórios, podem ser realizados testes adicionais para ampliar a validação do agente, como:

* testar diferentes combinações de gênero, ano, avaliação e temas;
* utilizar diferentes formas de escrita para uma mesma solicitação;
* testar mudanças de preferência durante a mesma conversa;
* verificar situações em que nenhum filme da base atende aos critérios;
* testar solicitações envolvendo diretores, avaliações e períodos específicos;
* avaliar o comportamento do agente diante de critérios conflitantes ou muito específicos.

Esses testes adicionais podem contribuir para verificar a consistência do comportamento do MovieBack em diferentes situações de uso.
