## Sobre o projeto

Este projeto apresenta uma análise de **regressão linear e multicolinearidade** aplicada a dados de uma usina, com o objetivo de compreender a relação entre variáveis ambientais e a variável alvo **PE**.

O notebook foi desenvolvido em **Google Colab** e utiliza Python para treinar um modelo de regressão linear com **Statsmodels**, calcular o **VIF (Variance Inflation Factor)** e analisar os resíduos do modelo com visualizações interativas em **Plotly**.

---

## Objetivo

O objetivo principal é demonstrar, na prática, como avaliar a presença de multicolinearidade em um modelo de regressão linear.

O projeto busca responder perguntas como:

- Quais variáveis explicativas possuem maior relação com a variável alvo?
- O modelo de regressão linear apresenta bom poder explicativo?
- Existe multicolinearidade relevante entre as variáveis independentes?
- Os resíduos apresentam comportamento adequado?
- Há sinais visuais de heterocedasticidade no modelo?

---

## Problema analisado

A base utilizada contém variáveis relacionadas ao funcionamento de uma usina. A variável alvo do modelo é:

- **PE**: variável dependente que representa a saída/produção de energia.

As variáveis explicativas utilizadas no modelo são:

- **AT**: temperatura ambiente;
- **V**: velocidade do vento;
- **AP**: pressão atmosférica;
- **RH**: umidade relativa.

A análise utiliza essas variáveis para ajustar um modelo de regressão linear e avaliar a qualidade estatística do modelo.

---

## Como funciona o projeto

O notebook segue as seguintes etapas:

### 1. Importação das bibliotecas

São importadas bibliotecas para manipulação de dados, divisão de treino e teste, modelagem estatística, cálculo de multicolinearidade e visualização.

Principais bibliotecas utilizadas:

- Pandas;
- Scikit-learn;
- Statsmodels;
- Plotly.

---

### 2. Leitura dos dados

O projeto carrega a base de dados `usina.csv`.

No notebook original, o arquivo é lido a partir do Google Drive:

```python
df = pd.read_csv('/content/drive/MyDrive/usina.csv')
```

Para executar localmente, recomenda-se colocar o arquivo dentro da pasta `data/` e alterar o caminho para:

```python
df = pd.read_csv('data/usina.csv')
```

---

### 3. Definição das variáveis

A variável alvo é definida como:

```python
y = df['PE']
```

As demais variáveis são utilizadas como variáveis explicativas:

```python
X = df.drop(columns=['PE'])
```

---

### 4. Separação em treino e teste

A base é dividida em dados de treino e teste com `train_test_split`.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=230
)
```

---

### 5. Regressão linear com Statsmodels

O modelo é treinado utilizando **OLS (Ordinary Least Squares)**.

```python
modelo = sm.OLS(y_train, X_train).fit()
```

A partir do resumo estatístico do modelo, são avaliados indicadores como:

- R²;
- R² ajustado;
- Estatística F;
- Coeficientes;
- Valores-p;
- Intervalos de confiança.

---

### 6. Análise de multicolinearidade com VIF

O projeto calcula o **Variance Inflation Factor (VIF)** para medir o grau de multicolinearidade entre as variáveis explicativas.

O VIF ajuda a identificar se uma variável independente está altamente correlacionada com as demais variáveis do modelo.

Interpretação geral:

- VIF abaixo de 5: baixa multicolinearidade;
- VIF entre 5 e 10: multicolinearidade moderada;
- VIF acima de 10: multicolinearidade elevada.

---

### 7. Análise de resíduos

O notebook também realiza análise visual dos resíduos do modelo.

São criados gráficos interativos para comparar:

- valores previstos versus valores reais;
- valores previstos versus resíduos.

Essa etapa ajuda a verificar se os erros do modelo apresentam comportamento aleatório e se há sinais de heterocedasticidade.

---

## Tecnologias utilizadas

- Python
- Google Colab
- Pandas
- Scikit-learn
- Statsmodels
- Plotly

---

## Estrutura do repositório

```text
power-plant-multicollinearity-regression/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── power_plant_multicollinearity_regression.ipynb
│
├── data/
│   └── .gitkeep
│
└── img/
    └── .gitkeep
```

> As pastas `data/` e `img/` possuem apenas arquivos `.gitkeep` para manter a estrutura do projeto no GitHub sem adicionar README interno.

---

## Como executar no Google Colab

1. Abra o notebook no Google Colab.
2. Faça upload do arquivo `usina.csv` ou monte o Google Drive.
3. Execute as células na ordem.
4. Analise o resumo do modelo, os valores de VIF e os gráficos de resíduos.

Depois que o projeto estiver no GitHub, você poderá abrir diretamente no Colab usando um link neste formato:

```text
https://colab.research.google.com/github/imarques-codes/power-plant-multicollinearity-regression/blob/main/notebooks/power_plant_multicollinearity_regression.ipynb
```

---

## Como executar localmente

Clone o repositório:

```bash
git clone https://github.com/imarques-codes/power-plant-multicollinearity-regression.git
```

Acesse a pasta do projeto:

```bash
cd power-plant-multicollinearity-regression
```

Crie um ambiente virtual:

```bash
python -m venv .venv
```

Ative o ambiente virtual:

```bash
# Windows
.venv\Scripts\activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Abra o notebook:

```bash
jupyter notebook notebooks/power_plant_multicollinearity_regression.ipynb
```

---

## Base de dados

O projeto utiliza o arquivo:

```text
usina.csv
```

Caso a base de dados não esteja no repositório, coloque o arquivo dentro da pasta `data/` e ajuste o caminho no notebook para:

```python
df = pd.read_csv('data/usina.csv')
```

---

## Principais aprendizados

Este projeto fortalece conhecimentos práticos em:

- Regressão linear com Python;
- Modelagem estatística com Statsmodels;
- Interpretação de resumo estatístico de modelos OLS;
- Avaliação de multicolinearidade com VIF;
- Separação de dados em treino e teste;
- Análise visual de resíduos;
- Identificação de possíveis problemas em modelos de regressão;
- Organização de projetos de dados para portfólio no GitHub.

---

## Possíveis melhorias futuras

- Adicionar a base `usina.csv` na pasta `data/`, caso a licença permita;
- Criar uma seção final com os principais insights estatísticos;
- Adicionar gráficos exportados na pasta `img/`;
- Comparar o modelo OLS com outros modelos de regressão;
- Avaliar métricas preditivas no conjunto de teste;
- Criar uma versão em inglês do README;
- Padronizar os títulos dos gráficos e labels das visualizações.

---

## Autor

**Igor Henrique Marques dos Santos**

- LinkedIn: [linkedin.com/in/igorhmarques](https://www.linkedin.com/in/igorhmarques/)
- GitHub: [github.com/imarques-codes](https://github.com/imarques-codes)
- E-mail: [igorhmsantos@gmail.com](mailto:igorhmsantos@gmail.com)

---

## Status do projeto

Projeto concluído como estudo prático de **Regressão Linear, Multicolinearidade e Análise de Resíduos com Python**.
