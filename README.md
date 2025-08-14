# 🧠 Projeto de Machine Learning - Predição de Renda (>50k ou ≤50k)

Este projeto foi desenvolvido como parte de um curso de Inteligência Artificial, com o objetivo de criar um **modelo de Machine Learning** capaz de prever se uma pessoa ganha **mais** ou **menos** de 50k por ano, com base em dados demográficos e profissionais.

---

## 🎯 Objetivo
O foco principal foi **maximizar a métrica F1-Score**, garantindo um bom equilíbrio entre **precisão** (precision) e **sensibilidade** (recall).  
Além disso, foram testadas diferentes arquiteturas baseadas em **árvores de decisão** para avaliar desempenho e interpretabilidade.

---

## 📂 Conjunto de Dados
O dataset foi dividido da seguinte forma:
- **Treino:** 70%
- **Validação:** 15%
- **Teste:** 15%

Cada arquivo contém **45.225 instâncias** e **15 atributos** originais, totalizando **45 atributos** após engenharia de variáveis.

---

## 🛠️ Pipeline de Desenvolvimento

### 🔹 Pré-processamento
- Tratamento de valores faltantes.
- Agrupamento de categorias raras.
- Detecção e tratamento de **outliers**.

### 🔹 Engenharia de Atributos
- **OrdinalEncoder** (`unknown_value=-1`) para variáveis categóricas — mais leve e adequado aos modelos baseados em árvores.
- **StandardScaler** para variáveis numéricas.

### 🔹 Balanceamento de Classes
- Aplicação de **SMOTEENN** dentro do pipeline para lidar com desbalanceamento.

### 🔹 Validação
- **Validação cruzada estratificada (Stratified K-Fold)** para avaliar a robustez dos modelos e evitar overfitting.

### 🔹 Otimização de Hiperparâmetros
- **RandomizedSearchCV** para busca eficiente de combinações.
- **Early stopping** para evitar overfitting.
- Salvamento dos melhores hiperparâmetros em **JSON** para reaproveitamento.

### 🔹 Stacking & Out-of-Fold (OOF)
- Criação de um **meta-modelo Logistic Regression** treinado sobre as probabilidades OOF geradas pelos modelos base.

### 🔹 Calibração & Thresholding
- **CalibratedClassifierCV** para ajustar as probabilidades.
- Otimização do threshold com base na curva **precision-recall**.

### 🔹 Ensemble
- Combinação ponderada das probabilidades dos 3 modelos para maximizar a F1.

### 🔹 Explainability (XAI)
- **SHAP** para interpretar a importância e contribuição de cada variável nas previsões.

---

## 🤖 Modelos Utilizados
Foram testados e comparados 3 algoritmos baseados em árvores de decisão:

1. **XGBoost**
2. **LightGBM**
3. **CatBoost**

---

## 📊 Resultados

**Conjunto de Teste**

🔹 **XGBoost**  
- F1-Score: `0.7180`  
- Recall: `0.7500`  
- Acertos: `4216` de `5642` (classe 0) | `1263` de `1684` (classe 1)  

🔹 **LightGBM**  
- F1-Score: `0.7175`  
- Recall: `0.7488`  
- Acertos: `4214` de `5642` (classe 0) | `1262` de `1684` (classe 1)  

🔹 **CatBoost**  
- F1-Score: `0.7159`  
- Recall: `0.7476`  
- Acertos: `4210` de `5642` (classe 0) | `1258` de `1684` (classe 1)  

📌 **Acurácia geral**: ~87%  

---

## 🚀 Próximos Passos
Ainda estou trabalhando neste projeto para:
- Explorar novos métodos de engenharia de atributos.
- Ajustar pesos do ensemble.
- Testar modelos híbridos.
- Melhorar a métrica **F1**.

---

## 📌 Tecnologias e Bibliotecas
- **Python**  
- **Pandas, NumPy, Scikit-learn**  
- **XGBoost, LightGBM, CatBoost**  
- **SHAP**  
- **Imbalanced-learn**  

---
