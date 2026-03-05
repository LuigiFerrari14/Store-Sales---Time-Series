# Store-Sales---Time-Series
Sales forecasting using time series and machine learning with feature engineering and model comparison (Baseline vs Random Forest).


# 📈 Store Sales Forecasting

Projeto de **previsão de vendas utilizando séries temporais e Machine Learning**.  
O objetivo é prever o total de vendas diárias de uma rede de lojas utilizando dados históricos, variáveis de calendário, feriados e preço do petróleo.

Este projeto faz parte do meu **portfólio de Data Science**.

---

# 📊 Objetivo

Construir modelos de Machine Learning capazes de **prever vendas futuras** e comparar seu desempenho com uma **baseline simples**, demonstrando ganho real de performance.

---

# 🗂 Dataset

O projeto utiliza dados inspirados no dataset **Store Sales (Kaggle)**.

Principais arquivos utilizados:

- `train.csv` → histórico de vendas
- `holidays_events.csv` → informação de feriados
- `oil.csv` → preço do petróleo ao longo do tempo

Essas variáveis ajudam a capturar fatores externos que influenciam as vendas.

---

# 🔧 Etapas do Projeto

## 1️⃣ Importação das bibliotecas

Principais bibliotecas utilizadas:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

---

## 2️⃣ Carregamento dos dados

Os datasets de vendas, feriados e preço do petróleo são carregados e preparados para análise.

---

## 3️⃣ Tratamento de dados

Alguns tratamentos realizados:

- Conversão de datas
- Remoção de feriados transferidos
- Preenchimento de valores faltantes no preço do petróleo
- Criação de variável binária para indicar feriados

---

## 4️⃣ Preparação dos dados

As vendas são **agregadas por dia**, permitindo analisar o comportamento temporal das vendas.

Também são realizados **merges com dados externos**:

- feriados
- preço do petróleo

---

# 🧠 Feature Engineering

Foram criadas variáveis para ajudar os modelos a capturar padrões temporais:

### Features de calendário

- `year`
- `month`
- `dayofweek`
- `is_weekend`

### Features temporais

- `time_index`
- `lag_7` → vendas da semana anterior
- `rolling_mean_7` → média móvel semanal

### Variáveis externas

- `is_holiday`
- `oil_rolling_30`

---

# 📊 Análise Exploratória

Foram gerados gráficos para entender os padrões nos dados:

- Série temporal de vendas
- Vendas por dia da semana
- Matriz de correlação entre variáveis

Isso ajuda a identificar **tendências, sazonalidade e relações entre variáveis**.

---

# ✂️ Train / Test Split

Para respeitar a natureza temporal dos dados:

- **Treino:** dados mais antigos
- **Teste:** últimos **90 dias**

Isso evita **data leakage** e simula previsão real de vendas futuras.

---

# 🤖 Modelos Utilizados

## 1️⃣ Linear Regression

Modelo simples usado como referência inicial.

Métricas avaliadas:

- MAE
- RMSE
- R²

Também foram analisados os **coeficientes das variáveis** para interpretar o modelo.

---

## 2️⃣ Random Forest

Modelo baseado em **árvores de decisão**, capaz de capturar relações não lineares.

Configuração utilizada:

- `n_estimators = 200`
- `random_state = 42`
- `n_jobs = -1`

Também foi analisada a **importância das features**.

---

# 📉 Baseline

Para validar se os modelos realmente aprendem algo útil, foi criada uma baseline simples:

**Previsão = vendas da semana anterior (`lag_7`)**

Exemplo de resultado:

Baseline RMSE: 145199
Random Forest RMSE: 89302


Isso indica que o modelo **aprende padrões reais nos dados**.

---

# 📊 Resultados

Comparação geral:

| Modelo | Desempenho |
|------|------|
| Baseline | Erro alto |
| Linear Regression | Melhor que baseline |
| Random Forest | Melhor desempenho |

O **Random Forest apresentou menor erro**, sugerindo que as vendas possuem **relações não lineares com as variáveis**.

---

# 🚀 Próximos Passos

Possíveis melhorias para o projeto:

- Pipeline com `sklearn`
- `TimeSeriesSplit` para validação temporal
- Cross-validation específica para séries temporais
- `StandardScaler`
- `GridSearch` para otimização de hiperparâmetros
- Testar modelos como:
  - XGBoost
  - LightGBM
  - Prophet

---

# 🛠 Tecnologias Utilizadas

- Python
- Pandas
- Numpy
- Matplotlib
- Seaborn
- Scikit-Learn

---

# 👨‍💻 Autor

**Luigi Ferrari**

Projeto desenvolvido para **portfólio de Cientista de Dados**.
