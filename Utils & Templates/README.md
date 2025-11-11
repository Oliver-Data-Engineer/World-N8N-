# 🌍 World [ N8N ] - Região: Utils & Templates 🛠️

> **A fundação modular que acelera a construção de novos mundos.**

---

## 🧭 Visão Geral da Região

Esta região é o arsenal de blocos de construção (building blocks) do "World". Ela não contém fluxos de negócios completos, mas sim os componentes reutilizáveis que garantem a padronização e a eficiência no desenvolvimento.

O objetivo estratégico é aplicar o princípio DRY (Don't Repeat Yourself). Os fluxos aqui são projetados para serem chamados por outros fluxos (via nó `Execute Workflow`) ou copiados como ponto de partida.

## 🗺️ O Mapa de Recursos

Catálogo de sub-fluxos, templates e snippets.

### Sub-Fluxos (Componentes Reutilizáveis)

Fluxos projetados para serem chamados por `Execute Workflow`.

1.  **[Nome do Sub-Fluxo 1] (ex: `sub_TratamentoDeErroPadrao`)**
    * **Missão:** Recebe dados de um nó de erro e envia uma notificação padronizada para o Slack.
    * **Input:** `[JSON com dados do erro]`
    * **Output:** `[Nenhum (apenas notificação)]`
    * **[Ver o README deste componente](./NomeDaPastaDoComponente/README.md)**


### Templates (Pontos de Partida)

Estruturas de fluxo prontas para copiar e adaptar.

1.  **[Nome do Template 1] (ex: `template_ETL_Basico`)**
    * **Estrutura:** Um fluxo pré-configurado com `Cron Job` -> `HTTP Request` -> `Split in Batches` -> `Google Sheets`.
    * **Objetivo:** Ponto de partida rápido para novos pipelines de dados.

---

### Snippets (Funções de Código)

Lógicas úteis para os nós `Code` e `Set`.

1.  **[Nome do Snippet 1] (ex: `snippet_FormatarData_DDMMYYYY`)**
    * **Descrição:** Função Javascript (para nó `Code`) que recebe um timestamp e retorna uma data formatada em `DD/MM/YYYY`.
    * **[Ver o README do Snippet](./Snippets/README.md#snippet-formatardata-ddmmyyyy)**

---

### [Retornar ao Mapa Principal (World N8N)](../README.md)
