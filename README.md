# IBM Data Analysis – House Prices Prediction

Projeto final do curso **Data Analysis with Python (IBM)**, com foco em aplicar as principais etapas de um pipeline de Ciência de Dados: análise exploratória, limpeza, visualização e modelagem preditiva.  
O objetivo foi prever o preço de venda de imóveis no condado de King (EUA), analisando os fatores que mais influenciam o valor final.


## Estrutura do Projeto

- **House_Sales_in_King_Count_USA.ipynb** – Notebook principal  
- **housing.csv** – Dataset utilizado  
- **README.md** – Documentação do projeto  
- **LICENSE** – Licença MIT


## Contexto

O dataset contém registros de vendas de imóveis no **King County (EUA)**, que inclui Seattle, entre maio de 2014 e maio de 2015.  
Cada linha representa uma propriedade e suas características físicas, geográficas e estruturais.

As principais variáveis incluem:
- `sqft_living`: área útil da casa (em pés²)  
- `bedrooms`, `bathrooms`: número de quartos e banheiros  
- `floors`: número de andares  
- `grade`: qualidade da construção  
- `sqft_above`: área útil acima do nível do solo  
- `sqft_living15`: média da área útil das 15 casas mais próximas  
- `price`: variável-alvo (preço de venda)


## Etapas do Projeto

### 1. Importação e Exploração Inicial
- Carregamento do dataset e inspeção de tipos de dados  
- Avaliação da distribuição das variáveis  
- Verificação de valores ausentes e duplicados

### 2. Limpeza e Preparação dos Dados
- Remoção de duplicatas  
- Conversão de tipos  
- Normalização e padronização de colunas numéricas  

### 3. Análise Exploratória e Visualização

A análise exploratória teve como objetivo identificar padrões, outliers e correlações relevantes.  
Alguns dos gráficos gerados durante o processo estão destacados abaixo:

#### Distribuição de Preços por Waterfront
![Distribuição de Preços por Waterfront](plots/boxplot_waterfront.png)

#### Relação entre Preço e Área Acima do Solo
![Relação entre Preço e Área Acima do Solo](plots/regplot_sqft_above.png)

#### Mapa de Correlação das Variáveis Numéricas
![Mapa de Correlação das Variáveis Numéricas](plots/correlation_heatmap.png)



### 4. Modelagem

Foram desenvolvidos e comparados diferentes modelos de **Regressão** para prever o preço de venda dos imóveis, utilizando uma abordagem incremental — começando com modelos simples e evoluindo para versões mais complexas e regulares.

#### 4.1 Regressões Lineares Simples
Inicialmente, foram testados modelos de **Regressão Linear simples**, utilizando uma variável por vez, com o objetivo de medir o poder explicativo individual de cada atributo em relação ao preço.

| Variável | R² |
|-----------|----|
| `long` (longitude) | 0.0004 |
| `sqft_living` (área útil) | 0.49 |

Essa análise preliminar indicou que a variável `sqft_living` apresenta forte relação linear com o preço, sendo uma das mais relevantes do conjunto.

#### 4.2 Regressão Linear Multivariada
Na etapa seguinte, foi construído um modelo de **Regressão Linear múltipla**, combinando as variáveis com maior correlação com o preço:

["floors", "waterfront", "lat", "bedrooms", 
 "sqft_basement", "view", "bathrooms", 
 "sqft_living15", "sqft_above", "grade"]

O modelo apresentou um R² ≈ 0.65, evidenciando melhora significativa em relação aos modelos univariados.


#### 4.3 Regressão Polinomial
Para capturar relações **não lineares** entre as variáveis e o preço, foi implementada uma **Pipeline polinomial** composta por:

- `StandardScaler()` → normalização dos dados  
- `PolynomialFeatures()` → geração de interações e termos de maior ordem  
- `LinearRegression()` → ajuste do modelo

O modelo polinomial alcançou um **R² ≈ 0.75**, mostrando ganho expressivo de desempenho em comparação às regressões lineares.

#### 4.4 Regularização com Ridge Regression
Para mitigar o overfitting observado nos modelos mais complexos, foi aplicada **Ridge Regression (α = 0.1)** em ambas as versões (linear e polinomial):

| Modelo | R² (aprox.) |
|--------|--------------|
| Ridge Linear | 0.64 |
| Ridge Polinomial (grau 2) | 0.70 |

Essa regularização ajudou a equilibrar **viés e variância**, resultando em previsões mais estáveis e generalizáveis.


### 5. Avaliação do Modelo

O modelo final — **Ridge Polinomial de grau 2 (α = 0.1)** — apresentou o melhor equilíbrio entre desempenho e robustez.  
As métricas foram calculadas sobre o conjunto de teste (15% dos dados):

- **R²:** 0.70  
- **RMSE:** ≈ 130.000  

Esses valores indicam que o modelo foi capaz de capturar cerca de **70% da variabilidade dos preços** com base nas variáveis estruturais e geográficas.  
O desempenho alcançado é adequado para o tipo de problema e demonstra a importância de considerar **relações não lineares** e **regularização** no ajuste de modelos preditivos.


## Tecnologias Utilizadas

- Python 3.10  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- Scikit-learn  


## Resultados e Insights

As variáveis com maior impacto sobre o preço foram:

| Variável | Correlação com o preço |
|-----------|------------------------|
| `sqft_living` | 0.70 |
| `grade` | 0.67 |
| `sqft_above` | 0.60 |
| `bathrooms` | 0.53 |

Esses fatores refletem a influência direta da metragem e da qualidade da construção no valor de mercado das propriedades.


## Certificado

Este projeto foi desenvolvido como parte do curso **Data Analysis with Python**, oferecido pela IBM.  
Abaixo, o certificado de conclusão do curso:

[📄 Clique aqui para visualizar o certificado](certificates/ibm-data-analysis-certificate.pdf)


---

## Autor

**Bernardo Corral**  
Estudante de Ciência de Dados  
[GitHub](https://github.com/BernardoCorral) • [LinkedIn](https://www.linkedin.com/in/bernardocorral/)



