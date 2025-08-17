# TelecomX — Relatório de Evasão de Clientes


## 1) Objetivo
Identificar os fatores que mais influenciam a evasão (churn) e comparar o desempenho dos modelos treinados no notebook fornecido, propondo ações de retenção com base nesses resultados.

## 2) Desempenho dos Modelos
**Regressão Logística**
- Acurácia: 0.75
- ROC AUC: 0.845
- Observação do notebook: *Recall da classe positiva elevado (~0,81), mas com precisão mais baixa (~0,52), indicando maior volume de falsos positivos.*

**Random Forest**
- Acurácia: 0.78
- ROC AUC: 0.824

**Leitura geral**
- O **Random Forest** apresentou **acurácia ligeiramente superior** à Regressão Logística (~0,78 vs ~0,75), enquanto a **Regressão Logística obteve ROC AUC ligeiramente maior** (~0,845 vs ~0,824). Em cenários de churn, o **recall** da classe positiva é crítico para identificar o maior número possível de clientes em risco. Assim, a escolha do modelo pode priorizar **recall/ROC AUC** (Logística) ou **acurácia** (RF), conforme a estratégia da área de negócios.

## 3) Principais Fatores de Evasão (a partir das variáveis selecionadas e achados do notebook)
1. **Tenure (tempo de relacionamento)**  
   Clientes com pouco tempo de casa têm **risco significativamente maior** de cancelar. A relação de Tenure com Churn foi descrita como **negativa** (quanto maior o tenure, menor o churn).

2. **Tipo de Contrato (Contract)**  
   **Contratos mensais** apresentam churn mais alto; **planos anuais/bianuais** reduzem a evasão por compromissos de prazo e benefícios agregados.

3. **Preço/Cobranças (MonthlyCharges / TotalCharges)**  
   **Cobranças mensais elevadas** aumentam o risco, especialmente em clientes novos. A sensibilidade a preço é um driver recorrente.

4. **Serviços de Internet e Suporte Técnico (InternetService, TechSupport)**  
   A presença/qualidade de **Suporte Técnico** e o **tipo de Internet** estão associados ao churn (sinais de insatisfação com a experiência).

> Observação: O notebook menciona que o **One-Hot Encoding** ampliou bastante o número de variáveis, o que dilui a leitura direta de importâncias, mas os padrões acima foram consistentes na análise descritiva e na comparação entre modelos.

## 4) Recomendações de Retenção Baseadas nos Resultados
**A. Onboarding e Cuidado com Clientes Novos (Tenure baixo)**  
- Programas de **boas-vindas nos 90 primeiros dias** com checagens proativas (NPS/CES curto) e **time de sucesso do cliente** para problemas iniciais.  
- **Ofertas de estabilidade**: bundle com benefícios (ex.: upgrade de velocidade por 3 meses) condicionado à permanência mínima.

**B. Migrar de Mensal para Longo Prazo (Contract)**  
- **Incentivos para migração**: desconto escalonado ou benefícios (ex.: roteador premium, canais extras) para **contrato anual/bianual**.  
- Comunicação clara de **economia total** no longo prazo para reduzir sensibilidade a preço.

**C. Gestão de Preço e Valor (MonthlyCharges/TotalCharges)**  
- **Segmentação por elasticidade**: clientes com alta sensibilidade recebem **ofertas personalizadas** (desconto temporário, ajuste de pacote).  
- **Bundles de valor** (combos) que elevam percepção de custo-benefício sem erosão excessiva de margem.

**D. Qualidade de Internet e Suporte (InternetService/TechSupport)**  
- **SLA de atendimento** específico para clientes em risco (prioridade na fila + callback em até X horas).  
- **Monitoramento proativo**: alertas de degradação de serviço → contato antes do cliente reclamar.  
- **Campanhas de ativação do TechSupport** (autoatendimento, visitas preventivas).

**E. Ações Operacionais Guiadas por Modelo (Recall alto)**  
- Adotar o **modelo com melhor ROC AUC/Recall** para **triagem semanal** de clientes em risco.  
- **Threshold ajustado por capacidade do time**: maximizar recall mantendo um volume de contatos tratável.  
- **Teste A/B**: comparar abordagem atual vs. abordagem guiada por modelo em métricas de churn a 30/60/90 dias e ROI de retenção.

## 5) Próximos Passos Sugeridos
1. **Matriz de custo** (falso positivo vs falso negativo) para calibrar o limiar de decisão por segmento.  
2. **Explicabilidade**: gerar **SHAP values** por cliente para razões de risco (ex.: preço alto + tenure baixo), facilitando o script de retenção do atendente.  
3. **Lista de alvos**: operacionalizar um **Top-N diário/semanal** com integração ao CRM (ID do cliente, score, motivos SHAP, playbook recomendado).  
4. **Monitoração**: acompanhar **drift** de dados e **re-treinar** modelo trimestralmente ou quando houver queda de AUC > X p.p.

---

### Anexo — Métricas capturadas do notebook
Regressão Logística — **Acurácia**: 0.75 | **ROC AUC**: 0.845  
Random Forest — **Acurácia**: 0.78 | **ROC AUC**: 0.824


