# 💳 Análise de Risco de Crédito com Machine Learning

## 📌 Visão Geral

A análise de risco de crédito desempenha papel fundamental no setor financeiro, auxiliando instituições na tomada de decisão sobre concessão de crédito e mitigação de perdas associadas à inadimplência. Em um cenário econômico desafiador, marcado pelo aumento do endividamento das famílias brasileiras, restrição de crédito e elevação do risco de inadimplência, torna-se cada vez mais importante o desenvolvimento de soluções analíticas capazes de identificar clientes com maior probabilidade de default de forma eficiente e operacionalmente viável.

Nesse contexto, instituições financeiras e fintechs buscam utilizar modelos estatísticos e técnicas de Machine Learning para apoiar decisões mais assertivas de concessão de crédito, reduzindo perdas financeiras, preservando a qualidade da carteira e equilibrando crescimento sustentável com controle de risco.

A capacidade de antecipar comportamentos de inadimplência tornou-se um diferencial estratégico, permitindo que as instituições ajustem políticas de crédito, limites, taxas e estratégias de mitigação de risco de acordo com o perfil de cada cliente.


## 🎯 Objetivo do Projeto

O objetivo deste projeto é desenvolver um modelo preditivo de Machine Learning capaz de prever a probabilidade de inadimplência (default) de clientes a partir de informações financeiras, cadastrais e comportamentais.

Para alcançar o objetivo proposto, foi desenvolvido um projeto completo de análise de risco de crédito, contemplando etapas de análise exploratória, tratamento e preparação dos dados, engenharia de atributos, seleção de variáveis, balanceamento de classes, otimização de hiperparâmetros e ajuste de thresholds. O processo teve como finalidade construir modelos preditivos robustos, interpretáveis e aderentes a cenários reais de concessão de crédito.

## 🛠️ Principais Etapas do Projeto


1. Análise Exploratória de Dados (EDA)

Análise exploratória voltada à compreensão do comportamento das variáveis, padrões associados à inadimplência, correlações e distribuição dos dados.

2. Divisão dos dados em conjuntos de treino e teste

Separação da base em conjuntos de treino e teste para garantir avaliação adequada da capacidade de generalização dos modelos.

3. Engenharia de Atributos (Feature Engineering)

Criação de novas variáveis derivadas com objetivo de aumentar a capacidade preditiva dos modelos.

Principais técnicas utilizadas:

- Binning de variáveis
- Weight of Evidence (WOE)
- Information Value (IV)
- Clusterização geográfica
- Variáveis agregadas
- Criação de variáveis comportamentais

4. Data Cleaning e tratamento lógico dos dados

Tratamento de inconsistências, ajuste de tipos de variáveis, tratamento de valores ausentes e outliers.

5. Pré-processamento dos dados

Aplicação de técnicas de transformação matemática e preparação dos dados para os algoritmos de Machine Learning.

Técnicas utilizadas:

- StandardScaler
- PowerTransformer (Yeo-Johnson)
- OneHotEncoder
- ColumnTransformer
- Pipelines do scikit-learn

6. Seleção de variáveis e construção dos conjuntos de modelagem

Avaliação comparativa entre diferentes estratégias de seleção de variáveis.

Conjuntos utilizados:

- Base completa
- Base reduzida por correlação de Pearson
- Base reduzida com SelectKBest

O objetivo desta etapa foi reduzir dimensionalidade, remover redundâncias e avaliar impacto das variáveis sobre desempenho, estabilidade e interpretabilidade dos modelos.

7. Modelagem

Treinamento e avaliação comparativa de diferentes algoritmos de classificação em cenário de dados desbalanceados.

Modelos avaliados:
- Logistic Regression
- Gaussian Naive Bayes
- Bernoulli Naive Bayes
- KNN
- SVC
- Decision Tree
- Random Forest
- Gradient Boosting
- Extra Trees
- Bagging
- XGBoost
- LightGBM
- CatBoost

Estratégias aplicadas: 

- Validação cruzada estratificada
- Class weighting
- SMOTE
- Métricas voltadas à classe minoritária
- Otimização de hiperparâmetros com Optuna
- Threshold tuning

Métricas utilizadas:
- Recall
- Precision
- ROC-AUC
- PR-AUC

## 📈 Principais Resultados

Após os experimentos realizados, os modelos LightGBM e SVC apresentaram os melhores resultados gerais utilizando a base reduzida por correlação de Pearson.

O modelo LightGBM demonstrou maior equilíbrio entre:

- Capacidade de detecção da inadimplência
- Estabilidade preditiva
- Controle de falsos positivos
- Eficiência operacional

Além disso, a análise de threshold tuning evidenciou a importância do trade-off entre Recall e Precision em cenários reais de risco de crédito.


## 💰 Avaliação de Custo de Decisão

O projeto também incorporou análise de custo de decisão considerando diferentes impactos operacionais entre:

- Falsos Positivos (FP)
- Falsos Negativos (FN)

Foi utilizada uma relação hipotética de custo:

- FP = 1
- FN = 10

Essa abordagem busca simular cenários reais de risco de crédito, nos quais aprovar clientes inadimplentes tende a gerar perdas significativamente maiores do que rejeitar clientes potencialmente adimplentes.

## 🚀 Possíveis Melhorias Futuras

Como oportunidades futuras de evolução, o projeto pode ser aprimorado com novas abordagens de modelagem, estratégias adicionais de avaliação e melhorias relacionadas ao contexto de negócio e operacionalização dos modelos.

Além disso, por se tratar de um problema complexo e amplamente explorado na área de risco de crédito, observações, sugestões e contribuições dos leitores e profissionais da área podem agregar novas perspectivas, auxiliar na identificação de pontos de melhoria e contribuir para a evolução contínua da solução proposta.

## 📚 Aprendizados

Este projeto proporcionou aprofundamento prático em:

- Análise exploratória de dados
- Engenharia de atributos
- Pré-processamento de dados
- Modelagem supervisionada
- Dados desbalanceados
- Otimização de hiperparâmetros
- Ajuste de threshold
- Avaliação de métricas em risco de crédito
- Interpretação de trade-offs operacionais

Mais do que maximizar métricas, o projeto contribuiu para desenvolver uma visão mais crítica sobre equilíbrio entre desempenho estatístico, viabilidade operacional e impacto de negócio em aplicações reais de Ciência de Dados.

<br>

> [Veja o notebook para detalhes da análise.](https://github.com/Gleynner/Analise_de_risco_de_credito/blob/main/Analise_Risco_de_Credito.ipynb)
