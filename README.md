# Detecção de Fraudes em Cartões de Crédito com Machine Learning

Este projeto aborda um dos problemas mais clássicos e desafiadores da ciência de dados: a **detecção de fraudes em transações financeiras**. O principal desafio deste cenário é o extremo desbalanceamento dos dados, visto que as fraudes representam uma fração minúscula do total de transações.

O objetivo deste repositório é demonstrar o desenvolvimento de um pipeline completo de Machine Learning, comparando diferentes algoritmos e aplicando técnicas avançadas de balanceamento, otimização e explicabilidade de modelos.

## 🛠️ Tecnologias e Bibliotecas Utilizadas

* **Linguagem:** Python
* **Manipulação de Dados:** Pandas e NumPy
* **Visualização Gráfica:** Matplotlib
* **Machine Learning:** Scikit-Learn e XGBoost
* **Balanceamento de Dados:** Imbalanced-Learn (SMOTE)
* **Explicabilidade (XAI):** SHAP (SHapley Additive exPlanations)

## 🏗️ Estrutura do Pipeline de Dados

O projeto foi construído seguindo uma linha lógica e organizada de desenvolvimento:

1. **Carregamento e Exploração:** Importação dos dados e análise do desbalanceamento crônico da variável alvo (`Class`).
2. **Engenharia de Atributos (Feature Engineering):** Aplicação de transformação logarítmica (`log1p`) e padronização de escala com `StandardScaler` na variável `Amount` (Valores das transações).
3. **Divisão Estratificada:** Separação dos dados em conjuntos de treino (70%) e teste (30%) utilizando amostragem estratificada para preservar a proporção de fraudes em ambas as partes.
4. **Modelagem Baseline:** Construção de um modelo inicial com Regressão Logística e avaliação por meio de métricas apropriadas (Relatório de Classificação, Curva ROC/AUC e Curva Precision-Recall).
5. **Técnicas de Balanceamento:** Implementação de estratégias de *Undersampling* (subamostragem) e *Oversampling* (superamostragem sintética via SMOTE).
6. **Algoritmos Avançados:** Treinamento e avaliação de modelos baseados em árvores e com pesos ajustados para dados desbalanceados:
   * **Random Forest Classifier** (`class_weight="balanced"`)
   * **XGBoost Classifier** (`scale_pos_weight`)
7. **Pipelines e Ajuste de Limiar (Threshold):** Criação de um fluxo integrado (`Pipeline`) unificando o pré-processamento ao modelo e experimentação de alteração do limiar de decisão de probabilidade (Custom Threshold = 0.3) visando otimizar o *Recall*.
8. **Otimização de Hiperparâmetros:** Utilização de `GridSearchCV` focado na métrica de *Recall* para extrair o máximo potencial do modelo XGBoost.
9. **Explicabilidade do Modelo (XAI):** Implementação da biblioteca SHAP para gerar gráficos de barras explicativos, demonstrando graficamente quais variáveis foram determinantes para as decisões de classificação da IA.

## 📊 Principais Descobertas e Resultados

*(Dica: Rode o seu notebook uma última vez do início ao fim, observe as métricas impressas nos Classification Reports e preencha os campos abaixo com os seus resultados reais!)*

* **Modelo Baseline (Regressão Logística):** Apresentou uma boa acurácia geral, porém com limitações no Recall para a classe de fraudes devido ao desbalanceamento bruto.
* **Ajuste de Threshold:** Reduzir o limiar para 0.3 permitiu capturar mais fraudes, elevando o Recall do modelo.
* **Random Forest & XGBoost:** Os modelos baseados em conjuntos de árvores (Ensembles) demonstraram maior robustez para lidar com o desbalanceamento inerente do dataset financeiro.
* **Importância das Variáveis (SHAP):** A análise de explicabilidade revelou de forma transparente quais componentes principais anonimizados (V1 a V28) e transformados tiveram o maior impacto preditivo no modelo final.

   ```bash
   git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)
