# Análise de Churn de Clientes - TelecomX

## Visão Geral do Projeto

Este projeto consiste em uma análise exploratória de dados e identificação dos principais fatores que influenciam a taxa de churn (cancelamento) de clientes da TelecomX. O objetivo é entender o comportamento dos clientes que cancelam seus serviços e fornecer insights que possam auxiliar a empresa a desenvolver estratégias de retenção mais eficazes.

## Fonte de Dados

Os dados utilizados nesta análise foram obtidos a partir de um arquivo JSON disponível publicamente. O dataset contém informações sobre clientes da TelecomX, incluindo dados demográficos, serviços contratados (telefone, internet, etc.), informações contratuais e dados de cobrança.

- **URL do Dataset:** `https://raw.githubusercontent.com/ingridcristh/challenge2-data-science/refs/heads/main/TelecomX_Data.json`

## Etapas da Análise

O notebook (`.ipynb`) deste repositório detalha as seguintes etapas da análise:

1.  **Extração:** Carregamento dos dados a partir do arquivo JSON.
2.  **Transformação:**
    *   Expansão das colunas que contêm dicionários (`customer`, `phone`, `internet`, `account`) em colunas separadas para facilitar o acesso aos dados aninhados.
    *   Renomeação de colunas com caracteres especiais (`Charges.Monthly` e `Charges.Total`).
    *   Tratamento de valores ausentes ou inconsistentes, como a substituição de valores vazios na coluna `ChargesTotal` e a conversão desta coluna para o tipo numérico.
    *   Criação de novas colunas para análise, como `Daily_Charges` e `TempoBase` (categorização do tempo de permanência do cliente).
3.  **Carga e Análise:**
    *   Análise da proporção geral de churn na base.
    *   Investigação da distribuição do churn por diferentes atributos dos clientes (gênero, senioridade, dependentes, tempo de base, tipo de contrato, serviços de telefone e internet, método de pagamento).
    *   Cálculo e comparação dos valores médios de cobrança mensal entre clientes com e sem churn.
    *   Cálculo da correlação entre variáveis numéricas relevantes (`tenure`, `ChargesMonthly`, `ChargesTotal`).
4.  **Visualização de Dados:**
    *   Geração de gráficos para ilustrar os principais achados da análise, incluindo:
        *   Proporção de Churn na Base (Gráfico de Rosca).
        *   Distribuição de Churn por Gênero, Senioridade, Dependentes e Gênero (Gráficos de Pizza).
        *   Distribuição do Churn por Tempo de Base (Gráfico de Barras).
        *   Distribuição do Churn por Tipo de Contrato vs Tempo de Base (Gráfico de Pizza e Barras Agrupadas).
        *   Análise de Churn por Serviços (PhoneService, InternetService) e Tempo de Base (Gráficos de Pizza e Barras Agrupadas).
        *   Análise de Churn por Método de Pagamento e Tempo de Base (Gráficos de Pizza e Barras Agrupadas).
        *   Análise de Valores Médios por Tempo de Base e Propensão ao Churn (Gráfico de Barras).

## Principais Resultados e Insights

A análise identificou diversos fatores que impactam a propensão ao churn, destacando-se:

*   A alta concentração de churn nos **primeiros meses de serviço**, especialmente em clientes com **contrato "Month-to-month"**.
*   Clientes que utilizam o serviço de **fibra óptica** e aqueles que pagam via **"Electronic check"** apresentam maior taxa de churn.
*   Clientes que cancelam geralmente possuem **valores de cobrança mensal mais elevados**.

Um relatório detalhado com as conclusões e recomendações pode ser encontrado no arquivo `Relatorio_Analise_Churn_TelecomX.md`.

## Como Executar o Notebook

Para replicar a análise, você pode abrir o notebook diretamente no Google Colab ou clonar este repositório e executá-lo em um ambiente Python com as bibliotecas necessárias instaladas (pandas, numpy, matplotlib, seaborn).

**Bibliotecas Necessárias:**
