# 🤖 Sentinela
## Agente Classificador de Feedback (NPS)

![n8n](https://img.shields.io/badge/n8n-Workflow-blueviolet?style=for-the-badge)
![Groq](https://img.shields.io/badge/Groq-LLM-blue?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-Logic-yellow?style=for-the-badge)
![Trello](https://img.shields.io/badge/Trello-Action-026AA7?style=for-the-badge)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-Storage-0F9D58?style=for-the-badge)
![Outlook](https://img.shields.io/badge/Outlook-Notify-0072C6?style=for-the-badge)

Este repositório contém um workflow de n8n de nível profissional para a automação completa do ciclo de vida de feedback de Net Promoter Score (NPS). O fluxo gerencia desde a captura da resposta do cliente até a análise por múltiplos agentes de IA, armazenamento em banco de dados e execução de ações de negócios distintas com base no resultado.

---

## 📄 A Solicitação (O Problema do Cliente)

Uma empresa de médio porte (ex: SaaS, E-commerce) nos procurou com o seguinte desafio:

> "Coletamos NPS de nossos clientes, mas o processo é totalmente manual. As respostas caem em uma planilha e, na melhor das hipóteses, olhamos para ela uma vez por mês. Não temos agilidade.
>
> **Nossa dor é:** Quando um **Detrator** nos dá um feedback valioso, só vemos dias depois, e o cliente já está perdido. Quando um **Promotor** nos elogia, perdemos a chance de agradecê-lo e engajá-lo. Nossos gerentes de produto gastam horas lendo comentários para tentar encontrar 'tendências', em vez de agir sobre elas.
>
> Precisamos de um sistema que leia o feedback por nós, nos diga o que é importante, e inicie ações *imediatamente*. Se o cliente está com raiva, queremos que uma tarefa seja criada para nossa equipe de Sucesso do Cliente *agora*, e queremos que o cliente saiba que foi ouvido. Se ele está feliz, queremos notificar nossa equipe de marketing. Precisamos fechar o loop do feedback."

---

## 🎯 A Dor que Este Projeto Resolve

Este workflow foi desenhado para eliminar o "cemitério de dados de feedback". Ele transforma o processo de NPS de uma **coleta passiva de dados** para um **sistema ativo e inteligente de ação**.

Ele resolve as seguintes dores:

* **Alta Latência de Resposta:** Reduz o tempo de resposta a um detrator de dias/semanas para segundos.
* **Feedback Não Acionável:** Converte comentários de texto livre (dados não estruturados) em insights estruturados (sentimento, categoria, motivador) que podem ser usados para criar painéis e tomar decisões.
* **"Loop Aberto" com o Cliente:** Garante que 100% dos clientes detratores recebam um reconhecimento e uma ação de acompanhamento, aumentando a retenção.
* **Custo de Análise Manual:** Libera as equipes de produto e sucesso do cliente da tarefa de ler e classificar manualmente centenas de comentários.

---

## 🛠️ Tecnologias Utilizadas

* **Orquestração:** n8n
* **Inteligência Artificial (LLM):** Groq (Modelo `llama-3.1-8b-instant`)
* **Processamento Lógico:** Python (em nós de Código do n8n)
* **Armazenamento de Dados:** Google Sheets
* **Notificações (Internas e Externas):** Microsoft Outlook
* **Gestão de Tarefas (Ação):** Trello
* **Coleta de Dados:** Formulário Web (Gatilho de n8n)

---
## 🗺️ Arquitetura (O Mapa do Workflow)

O fluxo de dados é linear e dividido em quatro estágios lógicos principais: Coleta, Enriquecimento, Armazenamento/Decisão e Ação.

```mermaid
graph TD
    A[Formulário NPS] --> B(Marco 1: Coleta e Classificação);
    B --> C(Marco 2: Enriquecimento via Cadeia de IA);
    C --> D(Marco 3: Armazenamento no Google Sheets);
    D --> E{Marco 4: Ramificação Switch};
    E --> F[Ramo Detrator];
    E --> G[Ramo Promotor];
    E --> H[Ramo Neutro];
    
    subgraph "Marco 5: Ações (Detrator)"
        F --> I(Enviar Email p/ Cliente);
        F --> J(Email Alerta Interno 🚨);
        F --> K(Criar Card no Trello);
    end
    
    subgraph "Marco 5: Ações (Promotor e Neutro)"
        G --> L(Email Notificação Interna 🎉);
        H --> M(Email Notificação Interna 📊);
    end
 ```
---

---

## 🖼️ Visuais / "Tour" do Workflow

Uma visão detalhada dos componentes visuais da automação, desde o fluxo de nós no n8n até os *templates* de comunicação enviados.

### 1. Mapa do Workflow (n8n)
<img width="1149" height="701" alt="image" src="https://github.com/user-attachments/assets/8f9de96e-8950-4a4c-8523-d4fb8b75002b" />


Imagens de cada bloco lógico principal dentro da interface do n8n.

* **Bloco 1: Coleta e Classificação NPS**
   <img width="1654" height="291" alt="image" src="https://github.com/user-attachments/assets/a0c18e11-1896-4fce-8fd7-d2e09b69a479" />

* **Bloco 2: Cadeia Multiagentes de IA (Groq)**
  <img width="1807" height="410" alt="image" src="https://github.com/user-attachments/assets/9134b9d0-3a0b-4cac-b310-b66d742f5b5d" />

* **Bloco 3: Armazenamento e Ramificação (Switch)**
   <img width="1721" height="486" alt="image" src="https://github.com/user-attachments/assets/6e35d6b1-b28e-4cd9-8d54-f1d8d4bfd51c" />


### 2. Templates de Notificação (Outlook)

Os *outputs* finais de comunicação, estilizados em HTML para diferentes cenários.

---

* **Alerta de Detrator 🚨 (Notificação Interna)**
  
<img width="461" height="820" alt="image" src="https://github.com/user-attachments/assets/d791476b-466b-4d79-a6f4-e890fdf576b1" />
    
---
* **Ação de Retenção 📨 (Email para o Cliente Detrator)**
  
<img width="431" height="430" alt="image" src="https://github.com/user-attachments/assets/9125df0b-cda3-48f4-a4d8-72b0821bff02" />

---

* **Notificação de Promotor 🎉 (Notificação Interna)**
  
<img width="456" height="841" alt="image" src="https://github.com/user-attachments/assets/a7dd45df-a803-4228-a3dd-a48dc9eb9c46" />

---

* **Ticket de Ação (Trello)**
<img width="610" height="814" alt="image" src="https://github.com/user-attachments/assets/ea709d3f-ec69-41be-a570-16d043f14050" />

---


## ⚙️ Funcionalidades Detalhadas (Passo a Passo)

O workflow é dividido em 4 etapas lógicas principais:

### 1. Etapa 1: Coleta e Preparação de Dados

Esta etapa captura a entrada do usuário e a prepara para a lógica de negócios.

* **Gatilho (Formulário):** Inicia o fluxo quando um usuário preenche o formulário "Pesquisa de satisfação" (Coleta: Email, Nome, Nota 0-5, Comentário).
* **Limpeza de Campos:** Renomeia variáveis brutas para nomes limpos (ex: `resposta_likert`, `cometario`).
* **Conversão de Dados (Python):** Converte a nota (string) em um número inteiro (integer) para permitir cálculos.
* **Classificação NPS (Python):** O cérebro da regra de negócio. Adiciona o campo `classificacao` com base na nota:
    * **0, 1, 2:** "Detrator"
    * **3:** "Neutro"
    * **4, 5:** "Promotor"
* **Formatação de Data:** Cria um registro de data legível (dd/M/yyyy).

### 2. Etapa 2: Enriquecimento com Multiagentes de IA (Groq)

Esta é a etapa de inteligência, onde o comentário de texto livre do cliente é analisado por uma cadeia de 4 agentes de IA, cada um com uma tarefa específica.

1.  **Agente Corretor:** Recebe o `cometario` original e o reescreve, corrigindo erros de ortografia, gramática e acentuação.
2.  **Agente Sentimento:** Analisa o comentário corrigido e o classifica como "Positivo", "Negativo" ou "Neutro" (via JSON).
3.  **Agente Categorias:** Analisa o comentário e o classifica em Categoria (ex: "Produto / Solução", "Atendimento / Suporte") e Subcategoria (ex: "Qualidade dos dados", "Tempo de resposta") (via JSON).
4.  **Agente Motivadores:** Identifica o "driver" principal (o motivo raiz) do feedback (ex: "Performance da plataforma", "Custo-benefício").

### 3. Etapa 3: Armazenamento e Ramificação

Com todos os dados em mãos (originais + IA), o fluxo os armazena e decide qual caminho seguir.

* **Registro (Google Sheets):** Adiciona uma nova linha na planilha "n8n-forms", salvando *todos* os dados: originais, classificação NPS e todas as saídas dos 4 agentes de IA.
* **Decisão (Switch):** Lê o campo `classificacao` e direciona a execução para um dos três ramos: "Detrator", "Promotor" ou "Neutro".

### 4. Etapa 4: Ações e Notificações (Os Ramos)

Esta etapa executa ações personalizadas com base na decisão do Switch.

#### ➡️ Ramo Comum: Promotor e Neutro

* **Template de Email (HTML):** Define um template HTML estilizado (Verde 🎉 para Promotor, Amarelo 📊 para Neutro).
* **Notificação Interna (Outlook):** Envia o e-mail HTML para a equipe interna, notificando sobre o novo feedback.

#### ➡️ Ramo Crítico: Detrator

Este é o fluxo de "fechamento de loop" e o mais complexo.

1.  **Template de Email (HTML):** Define um template HTML de alerta vermelho 🚨.
2.  **Notificação Interna (Outlook):** Envia o e-mail de alerta vermelho para a equipe interna *imediatamente*.
3.  **Email para o Cliente (Outlook):** Paralelamente, envia um e-mail HTML personalizado para o *cliente*, agradecendo o feedback, pedindo desculpas e informando que o caso está sendo analisado.
4.  **Ação (Trello):** Cria um novo card no Trello (ex: "Backlog Sucesso do Cliente").
    * **Descrição do Card:** O card é pré-preenchido com um template Markdown, contendo todos os dados do cliente, o comentário original, o comentário corrigido e toda a análise da IA (sentimento, categoria, motivador). Isso funciona como um ticket de ação para a equipe de Sucesso do Cliente.

---

## 🏁 Próximos Marcos (Roadmap) e Contribuição

Este projeto estabelece a fundação para um sistema de *Customer Experience* (CX) totalmente automatizado. Os próximos passos planejados focam em expandir a inteligência e a integração do *workflow*.

### Roadmap Estratégico

* **[ ] Dashboard de Insights:** Conectar a planilha do Google Sheets a uma ferramenta de BI (ex: Looker Studio, Power BI) para criar um *dashboard* em tempo real que visualize as tendências de "Categoria" e "Motivadores" identificadas pela IA.
* **[ ] Agente de Intenção (Detrator):** Adicionar um quinto agente de IA no ramo "Detrator" que analise o comentário e classifique a *intenção* do cliente (ex: "Solicitação de Reembolso", "Dúvida Técnica", "Churn Iminente"), permitindo rotear o *card* do Trello para equipes diferentes (Suporte, Financeiro, Sucesso do Cliente).
* **[ ] Integração com CRM:** Substituir o Google Sheets por uma integração direta com um CRM (ex: HubSpot, Salesforce), atualizando o registro do cliente com os *insights* gerados pela IA.
* **[ ] Personalização de Promotores:** Criar uma ação no ramo "Promotor" para enviar o feedback positivo diretamente a um canal de Slack (#elogios) ou solicitar ao cliente (via email) permissão para usar o comentário como depoimento.

### Como Contribuir ou Utilizar

1.  **Clone o Workflow:** Você pode utilizar o arquivo `.json` deste repositório e importá-lo diretamente no seu *canvas* do n8n.
2.  **Configure as Conexões:** Será necessário configurar suas próprias credenciais para Groq, Google Sheets, Trello e Outlook.
3.  **Implemente as Correções:** Antes de executar em produção, aplique as otimizações listadas na seção "Status do Projeto".
4.  **Contribua:** *Pull requests* são bem-vindos, especialmente para implementar os itens do *Roadmap*.
