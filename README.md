# Análise de dados utilizando Python

Análise do dataset Titanic, buscando destrinchar as variáveis e como se relacionam com os dados de saída.

### Passo a passo

### 0. Imports

- Inicialmente, importei as bibliotecas pandas, seaborn e o método pyplot da biblioteca matplotlib.

### 1. Carregando o conjunto de dados

- Carreguei o conjunto de dados Titanic;
- Apresentei as cinco primeiras linhas do dataset, verificando que foi carregado com sucesso.

### 2. Pré-processamento de dados

- Inicialmente, removi as seguintes colunas desnecessárias (basicamente duplicadas) e apresentei o dataset com as seguintes remoções:

1. **class:** A coluna pclass já apresenta a classe dos passageiros com valores numéricos, sendo mais simples do que valores categóricos;
2. **embarked_town:** A coluna embarked já apresenta o porto de embarque com valores categóricos mais simples;
3. **alive:** A coluna survived já responde se sobreviveu com valores númericos, sendo mais simples do que valores categóricos;
4. **alone:** As colunas sibsp/parch já detalham se o passageiro viajou com outras pessoas;
5. **who/adult_male**: As colunas sex/age já detalham o sexo e idade dos passageiros, sendo redundante ter colunas para identificar ser homem, mulher ou criança e se é adulto.

- Determinei a porcentagem de nulos das colunas e fiz o seguinte tratamento:

1. **age:** A coluna age apresentou valores nulos (menores que 90%), para escolher entre média e mediana, calculei a diferença se a diferença entre a média e a mediana representava menos de 5% do valor da mediana, como representou mais, optei por substituir os nulos pela mediana;
2. **embarked:** A coluna embarked apresentou valores nulos, como são menores que 20%, optei por substituir os nulos pela moda;
3. **deck:** A coluna deck apresentou bem mais de 50% de valores nulos, portanto, optei por remover a coluna.

- Verifiquei a presença de outliers nas colunas numéricas contínuas age, sibsp, parch e fare, e, como a análise busca determinar a relação entre as colunas e a coluna target survived, foi prudente deixar os outliers, pois um valor alto, como o da coluna fare (valor da passagem), pode indicar que condições financeiras impactaram na sobrevivência.

- Expus as estatísticas básicas para as colunas, obtendo o seguinte insight:

1. **survived:**
2. **pclass:**
3. **sex:**
4. **age:**
5. **sibsp:**
6. **parch:**
7. **fare:**
8. **embarked:**
