
<h1 align="center">
   💳 Análise de Risco de Crédito

 </h1>

<p align="center">
  `Python` `Scikit-learn` `LightGBM` `SVC` `Optuna` `Imbalanced-learn` `Feature Engineering (WOE/IV)`
</h1>

<p align="center">
  <img src="assets/Score-de-credito.png" width="670"/>
</p>


## 📌 Visão Geral

Projeto de Ciência de Dados para prever inadimplência de clientes, utilizando dados de uma competição promovida pela Nubank. O pipeline cobre todo o ciclo: análise exploratória, tratamento de dados, engenharia de atributos (incluindo Weight of Evidence e Information Value), seleção de variáveis, modelagem comparativa, otimização de hiperparâmetros com Optuna, ajuste de threshold e análise de custo de decisão orientada a negócio — com cuidado explícito na prevenção de data leakage e separação adequada entre treino e teste.


## 🎯 Objetivo

Desenvolver um modelo preditivo capaz de identificar clientes com maior probabilidade de inadimplência (default), equilibrando desempenho estatístico, estabilidade e viabilidade operacional para apoiar decisões de concessão de crédito.


## 📈 Resultados Principais

Após comparar 13 algoritmos de classificação em três estratégias de seleção de variáveis, **LightGBM** e **SVC** (com a base reduzida por correlação de Pearson) apresentaram o melhor desempenho geral no conjunto de teste:

| Modelo | Threshold | Recall (Inadimplente) | Precision (Inadimplente) | PR-AUC | Custo de Decisão* |
|---|---|:---:|:---:|:---:|:---:|
| **LightGBM** | Padrão | 0,84 | 0,22 | 0,211 | **6.045** ✅ |
| LightGBM | Ajustado | 0,91 | 0,20 | 0,193 | 6.140 |
| SVC | Padrão | 0,85 | 0,20 | 0,195 | 6.509 |
| SVC | Ajustado | 0,89 | 0,18 | 0,18 | 6.743 |

*\*Custo hipotético de decisão, simulando um cenário realista em que aprovar um cliente inadimplente (Falso Negativo) custa 10x mais do que rejeitar um bom cliente (Falso Positivo). Menor custo = melhor resultado operacional.*

✅ **Melhor resultado geral:** LightGBM com threshold padrão — menor custo operacional total entre todos os cenários avaliados, mesmo sem otimização agressiva do limiar de decisão. O ajuste de threshold aumentou o recall, mas à custa de mais falsos positivos e maior custo total — um trade-off relevante para decisões de negócio em risco de crédito.

O uso de SMOTE foi avaliado, mas descartado por não apresentar ganhos consistentes e 
pelo custo computacional elevado — a versão final utiliza apenas ponderação de classes 
(*class weights*).


## 🛠️ Etapas do Projeto

1. **Análise Exploratória de Dados** — investigação de padrões de inadimplência, correlações e distribuição das variáveis.
2. **Divisão treino/teste** — realizada antes de qualquer transformação, para evitar vazamento de dados.
3. **Data Cleaning** — tratamento de inconsistências, tipos de dados, valores ausentes e outliers (incluindo winsorização).
4. **Feature Engineering** — binning, Weight of Evidence (WOE), Information Value (IV), clusterização geográfica e variáveis derivadas.
5. **Pré-processamento** — `StandardScaler`, `PowerTransformer` (Yeo-Johnson), `OneHotEncoder` e `ColumnTransformer` dentro de Pipelines do scikit-learn.
6. **Seleção de Variáveis** — comparação entre base completa, redução por correlação de Pearson e `SelectKBest`.
7. **Modelagem** — 13 algoritmos avaliados (Logistic Regression, Naive Bayes, KNN, SVC, árvores, ensembles, XGBoost, LightGBM, CatBoost) com validação cruzada estratificada.
8. **Otimização e Threshold Tuning** — tuning de hiperparâmetros com Optuna e ajuste do limiar de decisão para os modelos finalistas (LightGBM e SVC).
9. **Análise de Custo de Decisão** — simulação de impacto financeiro de Falsos Positivos vs. Falsos Negativos.

> 📓 [Veja o notebook completo para todos os detalhes técnicos](https://github.com/Gleynner/Analise_de_risco_de_credito/blob/main/Analise_Risco_de_Credito.ipynb)


## 📊 Tecnologias

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `Scikit-learn` · `LightGBM` · `XGBoost` · `CatBoost` · `Optuna` · `Imbalanced-learn`


## 🚀 Próximos Passos

- Explorar estratégias adicionais de balanceamento além do SMOTE, que não apresentou ganhos consistentes neste problema.
- Avaliar modelos de custo-sensível (*cost-sensitive learning*) diretamente na etapa de treinamento.
- Testar a operacionalização do modelo (ex.: API de scoring) para simular uso em produção.

## 💡 Principal Aprendizado

Mais do que maximizar métricas, o projeto reforçou que o equilíbrio entre desempenho estatístico, viabilidade operacional e impacto de negócio é o que realmente define a qualidade de um modelo de risco de crédito — especialmente ao avaliar o trade-off entre Recall e Precision sob a ótica de custo real de decisão.

