# tech_challenger_fase3_fiap

# ✈️ Análise de Atrasos em Voos – Tech Challenge Fase 3

Este repositório apresenta o projeto desenvolvido para o **Tech Challenge – Fase 3 (Machine Learning Engineering)**, cujo objetivo é analisar dados públicos de voos nos Estados Unidos, aplicando técnicas de **análise exploratória de dados (EDA)**, **modelagem supervisionada** e **modelagem não supervisionada**, com foco na identificação de padrões de atraso, agrupamento de aeroportos e visualizações geográficas.

---

## 🎯 Objetivo do Projeto

O transporte aéreo é uma parte essencial da infraestrutura global, porém os atrasos impactam milhões de passageiros todos os anos.  
Este projeto busca:

- Explorar estatisticamente os dados de voos.
- Identificar fatores associados a atrasos.
- Agrupar aeroportos/rotas com comportamentos semelhantes.
- Visualizar padrões espaciais e operacionais.
- Avaliar limitações dos modelos e propor melhorias.

---

## 📊 Base de Dados

- **Fonte:** Dataset público de voos nos EUA (disponibilizado na Fase 3 do curso MLET).
- **Principais variáveis:**
  - Numéricas: `DISTANCE`, `SCHEDULED_TIME`, `ELAPSED_TIME`, `AIR_TIME`, `TAXI_OUT`, `TAXI_IN`, `DEPARTURE_DELAY`, `ARRIVAL_DELAY`, `DIVERTED`, `CANCELLED`
  - Categóricas: `AIRLINE`, `ORIGIN_AIRPORT`, `DESTINATION_AIRPORT`, `ORIGIN_CITY`, `DEST_CITY`
  - Geográficas: `ORIGIN_LATITUDE`, `ORIGIN_LONGITUDE`, `DEST_LATITUDE`, `DEST_LONGITUDE`

---

## 🧪 Etapas do Projeto

### 1️⃣ Exploração dos Dados (EDA)
- Estatísticas descritivas.
- Análise de distribuição de atrasos.
- Avaliação de aeroportos mais críticos.
- Tratamento de valores ausentes.
- Visualizações para extração de insights.

---

### 2️⃣ Modelagem Supervisionada e Não Supervisionada

  **Modelagem Supervisionad**:

### 🎯 Definição do Target para Supervisionada
Classificação binária:

- `DELAYED = 1` → atraso acima do limite (ex.: > 15 minutos)
- `DELAYED = 0` → voo pontual

  **Modelagem Não Supervisionada**

#### 🔹 Redução de Dimensionalidade (PCA)
- Aplicada sobre variáveis numéricas para reduzir dimensionalidade.
- Permitiu identificar os principais eixos de variabilidade operacional dos voos.

#### 🔹 Clusterização (DBSCAN)
- Aplicada sobre os componentes principais.
- Objetivo: agrupar voos e aeroportos com padrões semelhantes de atraso e operação.
- Identificação de:
  - **Clusters de voos regulares e eficientes**
  - **Clusters de alto atraso**
  - **Outliers (cluster -1)** representando situações atípicas

---

### 3️⃣ Análise dos Clusters

Foram calculadas métricas por cluster:

- Atraso médio de partida (`DEPARTURE_DELAY`)
- Atraso médio de chegada (`ARRIVAL_DELAY`)
- Tempo médio de taxi (`TAXI_OUT`, `TAXI_IN`)
- Taxa de cancelamento e desvios

📌 **Exemplo de interpretação:**
- Clusters com altos atrasos médios representam rotas/aeroportos críticos.
- Clusters com atrasos negativos indicam eficiência operacional.
- O cluster `-1` (outliers) concentra situações extremas e comportamentos irregulares.

---

### 4️⃣ Visualização Geográfica

#### 🌍 Mapas de Rotas
- Construção de mapas interativos com **Folium**.
- Representação de:
  - Rotas aéreas mais frequentes.
  - Atrasos médios por rota (cores indicam severidade).

#### 📍 Pontos de Aeroportos
- Exibição apenas dos **aeroportos**, com:
  - Cores baseadas no atraso médio.
  - Identificação de hubs mais críticos.

---

### 5️⃣ Identificação de Padrões Temporais
- Possibilidade de análise por:
  - Horário do dia.
  - Dias da semana.
  - Estações do ano.
- Identificação de **períodos críticos** com maior incidência de atrasos.

---

## 📈 Principais Resultados

- Identificação de **clusters distintos de desempenho operacional**.
- Destaque de aeroportos e rotas com **maiores atrasos médios**.
- Visualização espacial mostrou concentração de atrasos em grandes hubs.
- A clusterização permitiu separar:
  - Operações regulares.
  - Casos de atrasos severos.
  - Situações atípicas (outliers).

---

## ⚠️ Limitações

- **DBSCAN sensível a parâmetros (`eps`, `min_samples`)**.
- PCA reduz interpretabilidade direta das variáveis originais.
- Dataset não considera fatores externos como:
  - Clima.
  - Manutenção de aeronaves.
  - Controle de tráfego aéreo.
- Cancelamentos e desvios apresentaram baixa variabilidade.

---

## 🚀 Próximos Passos e Melhorias

- Criar **features derivadas**:
  - Período do dia (manhã, tarde, noite).
  - Estação do ano.
  - Indicadores de pico de tráfego.
- Implementar **modelos supervisionados**:
  - Classificação: prever se um voo irá atrasar.
  - Regressão: prever tempo de atraso.
- Comparar algoritmos (ex.: Random Forest, XGBoost, Regressão Linear).
- Construir **dashboard interativo** (Streamlit ou Power BI).
- Explorar:
  - Detecção de anomalias.
  - Aprendizado semi-supervisionado.

---

## 🛠️ Tecnologias Utilizadas

- **Python**
- **PySpark / Spark ML**
- **Pandas / NumPy**
- **Scikit-learn**
- **Matplotlib / Seaborn**
- **Folium (mapas interativos)**
- **Jupyter Notebook / Databricks**

---
