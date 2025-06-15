# Relatório de Análise de Churn - TelecomX

## Introdução

Este relatório apresenta uma análise aprofundada do churn de clientes da TelecomX, com o objetivo de identificar os principais fatores que contribuem para a evasão e fornecer insights para a retenção de clientes. A análise foi realizada com base nos dados fornecidos, abrangendo características do cliente, serviços utilizados, informações contratuais e financeiras.

## Análise Exploratória e Limpeza de Dados

Inicialmente, os dados brutos foram carregados e expandidos para facilitar a análise. Foram identificados e tratados valores ausentes e inconsistências, como o preenchimento de valores vazios na coluna `ChargesTotal` utilizando a multiplicação de `tenure` por `ChargesMonthly` para clientes com tempo de base zero, assumindo que se tratam de novos clientes com cobrança total ainda não registrada. A coluna `ChargesTotal` foi convertida para o tipo numérico (`float64`) para permitir cálculos e análises estatísticas. Não foram encontradas duplicidades na base.

## Principais Ofensores e Insights

A análise revelou que a taxa geral de churn na base da TelecomX é de **25.72%**. A investigação dos diferentes atributos dos clientes permitiu identificar os seguintes ofensores e insights relevantes:

### 1. Características Pessoais

*   **Gênero e Senioridade:** A distribuição do churn por gênero é equitativa entre homens e mulheres. No entanto, clientes **não-idosos** representam a maior parcela do churn, indicando que a senioridade por si só não é um fator determinante isolado.
*   **Dependentes:** Clientes **sem dependentes** apresentam uma maior propensão ao churn, independentemente do gênero.

### 2. Tempo de Base (Tenure)

*   A distribuição do churn por tempo de base é um dos fatores mais críticos. Há uma concentração significativa de churn nos **primeiros 24 meses**, especialmente nos **primeiros 4 meses (9.36% do churn total)**.
*   Observa-se uma redução do churn em períodos intermediários, com um **novo aumento após 36 meses**, sugerindo que a propensão ao churn varia ao longo do ciclo de vida do cliente.

### 3. Tipo de Contrato

*   O tipo de contrato é um dos principais impulsionadores do churn. O contrato **"Month-to-month"** é responsável por aproximadamente **88.5% do churn total**.
*   Esta modalidade contratual é predominante no churn, especialmente nas faixas iniciais de tempo de base (até 9 meses).
*   Contratos de longo prazo (**"One year"** e **"Two year"**) apresentam taxas de churn significativamente menores.

### 4. Serviços Contratados

*   **Serviço de Telefonia (`PhoneService`):** Clientes que possuem o serviço de telefonia (`Yes`) representam a vasta maioria do churn (cerca de 92% do churn total).
*   **Serviço de Internet (`InternetService`):** Clientes com serviço de **fibra óptica (`Fiber optic`)** são os maiores contribuintes para o churn (17.85% do total), representando 69.4% do churn relacionado a serviços de internet. A participação da fibra óptica no churn é distribuída por todas as faixas de tempo de base.

### 5. Método de Pagamento

*   O método de pagamento **"Electronic check"** está associado a uma parcela significativa do churn (14.72%), representando 57% do churn total. Embora outros métodos de pagamento também contribuam, o "Electronic check" se destaca como um ofensor importante.

### 6. Valores Cobrados (`ChargesMonthly` e `ChargesTotal`)

*   Clientes que cancelam (`Churn = Yes`) possuem **valores médios de cobrança mensal (`ChargesMonthly`) significativamente mais altos** do que clientes que não cancelam (`Churn = No`). Em média, clientes que cancelam pagam cerca de $13 a mais por mês.
*   Essa diferença nos valores médios se mantém e até se acentua ao longo do tempo de base, indicando que o valor pago está correlacionado com a propensão ao churn.

## Conclusões e Recomendações

Com base na análise realizada, os principais ofensores e motivos para a propensão ao churn na TelecomX são:

*   **Contrato Month-to-month:** A flexibilidade deste contrato, embora atrativa inicialmente, representa um alto risco de churn, especialmente para clientes novos.
*   **Tempo de Base Inicial:** Os primeiros meses são críticos para a retenção, com alta taxa de churn em clientes com menos de 4 meses de serviço.
*   **Serviço de Fibra Óptica:** Clientes que utilizam fibra óptica, apesar de possivelmente representarem um segmento de maior valor, apresentam maior propensão ao churn.
*   **Método de Pagamento Electronic Check:** A associação deste método de pagamento com altas taxas de churn sugere possíveis problemas na experiência do cliente com este método.
*   **Valores Elevados:** Clientes com contas mensais mais altas são mais propensos a cancelar, indicando que a percepção de valor ou a satisfação com o custo-benefício pode ser um fator.

**Recomendações:**

1.  **Foco na Retenção Inicial:** Desenvolver estratégias de engajamento e suporte intensivo para clientes nos primeiros 6-12 meses, especialmente aqueles com contrato "Month-to-month".
2.  **Análise do Serviço de Fibra Óptica:** Investigar as causas específicas do alto churn entre usuários de fibra óptica. Pode estar relacionado à qualidade do serviço, suporte técnico, ou expectativas não atendidas.
3.  **Experiência com Electronic Check:** Analisar o processo e a experiência do cliente ao utilizar o método de pagamento "Electronic check" para identificar e resolver possíveis pontos de atrito.
4.  **Segmentação por Valor:** Implementar estratégias de retenção diferenciadas para clientes de alto valor, buscando entender suas necessidades e preocupações que podem levar ao churn.
5.  **Incentivo a Contratos de Longo Prazo:** Oferecer benefícios e incentivos atrativos para migração de contratos "Month-to-month" para contratos de um ou dois anos, reduzindo a flexibilidade de cancelamento.

Este relatório fornece um ponto de partida para a TelecomX desenvolver ações direcionadas para mitigar o churn e melhorar a retenção de clientes, focando nos segmentos e fatores de maior risco identificados.