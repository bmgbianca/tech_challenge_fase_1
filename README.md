# Tech Challenge — Fase 1

Projeto de machine learning para classificação do diagnóstico de **Síndrome do Ovário Policístico (SOP)** a partir de dados clínicos e laboratoriais de pacientes.

---

## Sobre o Projeto

A Síndrome do Ovário Policístico (SOP) é uma condição hormonal comum que afeta mulheres em idade reprodutiva. O objetivo deste projeto é treinar e avaliar modelos de classificação capazes de prever se uma paciente tem ou não SOP com base em suas características clínicas, laboratoriais e de estilo de vida.

---

## Dataset

**Arquivo:** `PCOS_DataSet.xlsx`  
**Amostras:** 684  
**Features:** 32 variáveis preditoras (numéricas e categóricas)  
**Variável-alvo:** `PCOS` (0 = Sem SOP / 1 = Com SOP)

O dataset é **desbalanceado**, com aproximadamente **76,2% das amostras diagnosticadas com SOP**.

---

## Estrutura do Repositório

```
tech_challenge_1/
├── dataset/
│   └── PCOS_DataSet.xlsx
├── notebook/
│   └── BIANCA_DE_MORAES_GOMES_tech_challenge_1.ipynb
└── README.md
```

---

## Metodologia

### 1. Análise Exploratória dos Dados (EDA)
- Identificação de dados ausentes "disfarçados" com respostas como `"I do not know"` em ~25% das colunas
- Análise de correlação entre ausência de dados e a variável-alvo
- Detecção e tratamento de outliers nas variáveis numéricas (peso, altura, IMC)
- Análise do desbalanceamento da variável-alvo
- Mapas de calor cruzando variáveis categóricas com a variável-alvo para identificar features relevantes

### 2. Pré-processamento
- Tratamento de dados ausentes e outliers
- Separação treino/teste (80/20) com `stratify` para preservar a proporção das classes
- Codificação de variáveis categóricas binárias com `OrdinalEncoder`
- Codificação de variáveis categóricas não-binárias com `OneHotEncoder` (com `drop='first'`)
- Escalonamento das variáveis numéricas com `MinMaxScaler`
- Redução de dimensionalidade com **PCA (25 componentes)** — capturando a maior parte da variância

### 3. Modelos Treinados

| Modelo | Detalhes |
|---|---|
| **KNN** | `n_neighbors=5`, com PCA aplicado |
| **SVC** | `kernel='poly'`, `class_weight='balanced'`, sem PCA |
| **Random Forest** | `criterion='gini'`, `class_weight='balanced_subsample'`, com PCA |

A escolha dos hiperparâmetros (valor de K, kernel do SVC e critério do Random Forest) foi feita por análise da taxa de erro em diferentes configurações.

### 4. Avaliação
Os modelos foram avaliados com `classification_report` do scikit-learn, analisando:
- Precision
- Recall
- F1-score
- Acurácia geral

---

## Tecnologias e Bibliotecas

- Python
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- plotly
- missingno

---

## Como Executar

1. Clone o repositório:
   ```bash
   git clone <url-do-repositório>
   ```

2. Instale as dependências:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn plotly missingno openpyxl
   ```

3. Abra e execute o notebook:
   ```bash
   jupyter notebook notebook/BIANCA_DE_MORAES_GOMES_tech_challenge_1.ipynb
   ```

---

## Autora

**Bianca de Moraes Gomes**  
Tech Challenge — Pós-graduação em Inteligência Artificial
