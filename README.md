# Análise Preditiva de Evasão de Clientes (Churn) em Telecom

![Análise de Dados](https://img.shields.io/badge/Análise_de_Dados-Python-blue)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-Scikit--Learn-orange)
![Licença](https://img.shields.io/badge/License-MIT-green)

## 📖 Visão Geral do Projeto

Este projeto tem como objetivo realizar uma análise completa sobre um conjunto de dados de uma empresa de telecomunicações para prever a evasão de clientes (churn). Através da análise exploratória, pré-processamento de dados e construção de modelos de Machine Learning, identificamos os principais fatores que levam os clientes a cancelarem seus serviços e desenvolvemos um sistema capaz de prever futuros cancelamentos.

## 📊 Sobre o Dataset

O conjunto de dados utilizado (`dados_telecom_tratados.csv`) contém informações demográficas, detalhes dos serviços contratados, informações de faturamento e o status de evasão de cada cliente. A variável alvo é a coluna `Churn`, onde `1` representa um cliente que evadiu e `0` um cliente que permaneceu.

## ⚙️ Metodologia e Pipeline da Análise

O projeto foi estruturado seguindo as melhores práticas de um ciclo de vida de projetos de Data Science:

1.  **Análise Exploratória de Dados (EDA):**
    * Investigação inicial para entender a distribuição dos dados.
    * Cálculo da proporção de churn (26.5% de evasão), identificando o desbalanceamento das classes.
    * Análise de correlação entre as variáveis numéricas para identificar relações iniciais com a evasão.

2.  **Pré-processamento e Limpeza:**
    * Remoção de colunas irrelevantes (ex: `ID_Cliente`).
    * **Encoding de Variáveis Categóricas:** Transformação de colunas de texto (como 'Gênero', 'Tipo de Contrato') em formato numérico utilizando a técnica de *One-Hot Encoding*.

3.  **Balanceamento de Classes:**
    * Aplicação da técnica de *Oversampling* na classe minoritária (clientes que evadiram) para criar um conjunto de dados balanceado, garantindo que os modelos não sejam enviesados em favor da classe majoritária.

4.  **Normalização/Padronização de Dados:**
    * Padronização das features numéricas utilizando `StandardScaler` para modelos sensíveis à escala, como a Regressão Logística.

5.  **Modelagem e Treinamento:**
    * Divisão dos dados em conjuntos de **treino (70%)** e **teste (30%)**.
    * Treinamento de dois modelos distintos para comparação:
        * **Random Forest Classifier:** Modelo robusto baseado em árvores, que não requer padronização dos dados.
        * **Regressão Logística:** Modelo linear clássico, treinado com os dados padronizados.

6.  **Avaliação dos Modelos:**
    * Análise de métricas como Acurácia, Precisão, Recall, F1-Score e Matriz de Confusão.
    * Verificação de overfitting comparando o desempenho nos dados de treino e teste.

7.  **Análise de Importância das Variáveis (Feature Importance):**
    * Extração e análise dos coeficientes da Regressão Logística e da importância das variáveis do Random Forest para entender os principais fatores de evasão.

## 🚀 Modelos e Resultados

| Modelo | Acurácia (Teste) | F1-Score (Teste) | Overfitting |
| :--- | :---: | :---: | :---: |
| **Random Forest** | ~86.6% | ~87.4% | Sim (requer ajuste) |
| **Regressão Logística** | ~75.9% | ~76.8% | Não |

O **Random Forest** obteve o melhor desempenho preditivo, mas demonstrou overfitting. A **Regressão Logística** se mostrou mais estável, embora menos precisa. Para uma implementação final, o Random Forest seria a escolha ideal após um processo de ajuste de hiperparâmetros.

## 🔑 Principais Fatores de Evasão Identificados

A análise de ambos os modelos convergiu para os seguintes fatores como os mais impactantes na decisão de um cliente evadir:

1.  **Tipo de Contrato:** Contratos `Month-to-month` são o principal indicador de risco.
2.  **Tempo de Contrato:** Clientes com poucos meses de casa têm altíssima probabilidade de sair.
3.  **Serviço de Internet:** Clientes com `Fibra Ótica` apresentam maior taxa de churn.
4.  **Taxa Mensal:** Valores mensais mais altos aumentam o risco.
5.  **Serviços Adicionais:** A ausência de serviços como `Suporte Técnico` e `Segurança Online` está correlacionada com maior evasão.

## 💡 Recomendações Estratégicas

Com base nas descobertas, foram propostas as seguintes estratégias de retenção:

* **Incentivar a migração** de contratos mensais para planos de longo prazo.
* Implementar um **programa de fidelidade** focado nos primeiros meses do cliente.
* Criar **pacotes de serviços** de suporte e segurança para aumentar o engajamento.
* Utilizar o modelo preditivo para **identificar clientes em risco** e direcionar ações de retenção.

## 🛠️ Como Executar o Projeto

Para replicar esta análise, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/lWolgrand/alura-challenger-telecomx2
    cd NOME_DO_REPOSITORIO
    ```

2.  **Crie um ambiente virtual (recomendado):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows: venv\Scripts\activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install pandas scikit-learn matplotlib seaborn
    ```

4.  **Execute o notebook:**
    * Abra o arquivo `.ipynb` (ex: `analise_churn.ipynb`) em um ambiente como Jupyter Notebook, JupyterLab ou Google Colab.
    * Certifique-se de que o arquivo `dados_telecom_tratados.csv` esteja no mesmo diretório.
    * Execute as células sequencialmente.

## 📁 Estrutura do Repositório

```
.
├── dados_telecom_tratados.csv      # Conjunto de dados original
├── analise_churn.ipynb             # Notebook com todo o código da análise
└── README.md                       # Documentação do projeto
```

---