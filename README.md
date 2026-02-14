# Análise de dados utilizando Python

Análise do dataset Titanic, buscando destrinchar as variáveis e como se relacionam com os dados de sobrevivência.

### Passo a passo

### 0. Imports

- Inicialmente, importei as bibliotecas pandas, seaborn e o método pyplot da biblioteca matplotlib.

### 1. Carregando o conjunto de dados

- Carreguei o conjunto de dados Titanic;
- Apresentei as cinco primeiras linhas do dataset, verificando que foi carregado com sucesso.

### 2. Pré-processamento de dados

- Removi as seguintes colunas desnecessárias (basicamente duplicadas) e apresentei o dataset com as seguintes remoções:

1. **class:** A coluna pclass já apresenta a classe dos passageiros com valores numéricos, sendo mais simples do que valores categóricos;
2. **embarked_town:** A coluna embarked já apresenta o porto de embarque com valores categóricos mais simples;
3. **alive:** A coluna survived já responde se sobreviveu com valores númericos, sendo mais simples do que valores categóricos;
4. **alone:** As colunas sibsp/parch já detalham se o passageiro viajou com outras pessoas;
5. **who/adult_male**: As colunas sex/age já detalham o sexo e idade dos passageiros, sendo redundante ter colunas para identificar ser homem, mulher ou criança e se é adulto.

- Determinei a porcentagem de nulos das colunas e fiz o seguinte tratamento:

1. **age:** A coluna age apresentou valores nulos (menores que 90%), para escolher entre média e mediana, calculei a diferença se a diferença entre a média e a mediana representava menos de 5% do valor da mediana, como representou mais, optei por substituir os nulos pela mediana;
2. **embarked:** A coluna embarked apresentou valores nulos, como são menores que 20%, optei por substituir os nulos pela moda;
3. **deck:** A coluna deck apresentou bem mais de 50% de valores nulos, portanto, optei por remover a coluna.

- Verifiquei a presença de outliers nas colunas numéricas contínuas age, sibsp, parch e fare, e, como a análise busca determinar a relação entre as colunas e a coluna target survived, foi prudente deixar os outliers. Antes de prosseguir, verifiquei a relação entre o valor de pagamento (fare) e classe (pclass), para verificar se o valor alto representava algum erro, e, como todas as três ocorrências do valor representaram pessoas da primeira classe, julguei prudente manter os outliers.

- Expus as estatísticas básicas para as colunas, obtendo o seguinte insight:

1. **survived:** Somente aproximadamente 38,38% dos passageiros conseguiram sobreviver;
2. **pclass:** A grande maior dos passageiros era de terceira classe (aprox. 51,11%), representando mais que a soma entre passageiros da primeira (aprox. 24,24%) e segunda classe (aprox. 20,65%);
3. **sex:** aprox. 64,76% dos passageiros eram do sexo masculino;
4. **age:** A média para essa variável não é confiável. Ao menos 75% dos passageiros possuem entre 0,42 (5,04 meses) e 35 anos, enquanto o maior valor é 80, evidenciando uma discrepância crescente, que implica na média não confiável; 
5. **sibsp:** A média para essa variável não é confiável. Ao menos 75% dos passageiros possuem entre 0 e 1 esposos (as)/irmãos, enquanto o maior valor é 8, evidenciando uma discrepância crescente, que implica na média não confiável;
6. **parch:** A média para essa variável não é confiável. Ao menos 75% dos passageiros possuem 0 pais/filhos, enquanto o maior valor é 6, evidenciando uma discrepância crescente, que implica na média não confiável;
7. **fare:** A média para essa variável não é confiável. Ao menos 75% dos passageiros desembolsaram entre £ 0 e £ 31, enquanto o maior valor foi aproximadamente £ 512,33, evidenciando uma discrepância crescente extremamente alta no valor que alguns passageiros pagaram, que implica na média não confiável;
8. **embarked:** A grande maioria (aprox. 72.50%) embarcaram no porto de Southampton.

### 3. Mineração de dados

- Fiz análise univariada de todas as colunas além da target "survived", pois as julguei como potencialmente importantes, sendo assim colunas-chave:

1. **age:** Distribuição dissimétrica com vários picos, sendo o maior entre valores próximos a 30 anos; o histrograma mostra que a completude de idades é enorme, desde bebês com meses de idade (um pico significativo) a idosos de 80 anos, com os maiores picos de idade sendo entre 20 e 40 anos;
2. **sibsp:** Distribuição assimétrica à direita (com pequenas excessões), com a grande maioria dos passageiros tendo um número menor (0) de irmãos/esposos (as) no navio, mas alguns tendo um número significativamente maior;
3. **parch:** Distribuição assimétrica à direita (com pequenas excessões), com a grande maioria dos passageiros tendo um número menor (0) de pais/filhos no navio, com alguns tendo um número significativamente maior;
4. **fare:** Distribuição assimétrica à direita, com a grande maioria dos passageiros tendo pagado um valor menor nas passagens, com alguns tendo pagado um número bem maior;
5. **pclass:** Mesma interpretação da feita nas estastísticas básicas, mostrando visualmente que os passageiros de terceira classe representam mais que a soma dos passageiros de primeira e segunda classe que embarcaram; 
6. **sex:** Mesma interpretação da feita nas estastísticas básicas, mostrando visualmente que o número de passeiros homens aparenta ser quase o dobro comparado ao de mulheres;
7. **embarked:** Mesma interpretação da feita nas estastísticas básicas, mostrando visualmente que poucos embarcaram em Cherbourg e Queenstown, com os embarques em Southampton representando bem mais que o somatório dos que embarcaram nas outras localidades.

- Fix análise bivariada