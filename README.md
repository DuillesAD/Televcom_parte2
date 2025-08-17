# 📘 Projeto: Análise de Evasão de Clientes (TelecomX) Parte 2

## 📌 Descrição
Este projeto tem como objetivo analisar os fatores que influenciam a **evasão de clientes (churn)** em uma empresa de telecomunicações e avaliar diferentes modelos de Machine Learning para prever o risco de cancelamento.

O trabalho foi desenvolvido em Python em formato **Jupyter Notebook**, com foco em:
- Exploração dos dados (EDA).
- Identificação de variáveis mais relevantes para churn.
- Treinamento e avaliação de modelos de classificação.
- Proposição de estratégias de retenção baseadas nos resultados.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas
- **Python 3**
- Pandas, Numpy
- Matplotlib, Seaborn (visualização)
- Scikit-learn (modelagem)
- Imbalanced-learn (tratamento de classes desbalanceadas)
- Jupyter Notebook

---

## 📂 Estrutura do Projeto

📁 TelecomX
├── TelecomX_parte2.ipynb # Notebook principal de análise
├── data/ # (opcional) Diretório para armazenar dataset
├── Relatorio_Evasao_TelecomX.md # Relatório detalhado (gerado)
└── README.md # Este arquivo


---

## 📊 Resultados Principais

### Desempenho dos Modelos
- **Regressão Logística**
  - Acurácia ~0.75 | ROC AUC ~0.84
  - Recall alto (detecta mais clientes em risco), mas baixa precisão.

- **Random Forest**
  - Acurácia ~0.78 | ROC AUC ~0.82
  - Melhor acurácia geral, porém menor recall para churn.

➡️ **Resumo**:  
A Regressão Logística é mais eficaz para identificar clientes em risco (alto recall), enquanto o Random Forest tem melhor desempenho em acurácia geral.

### Principais Fatores que Influenciam a Evasão
1. **Tempo de Contrato (Tenure)** — clientes recentes têm maior probabilidade de churn.  
2. **Tipo de Contrato** — contratos mensais têm mais evasão que anuais/bianuais.  
3. **Gastos (MonthlyCharges / TotalCharges)** — clientes com mensalidades altas e baixo gasto acumulado são mais propensos a cancelar.  
4. **Serviços de Internet e Suporte Técnico** — qualidade percebida do serviço impacta diretamente o churn.

---

## 🎯 Estratégias de Retenção Recomendadas
- **Onboarding ativo** nos 90 primeiros dias de contrato.  
- **Incentivos para migração** de planos mensais para anuais/bianuais.  
- **Gestão de preço personalizada** para clientes sensíveis a custos.  
- **Suporte técnico proativo** e campanhas de engajamento.  
- **Uso operacional dos modelos preditivos** para gerar listas de clientes em risco e guiar ações de retenção.
