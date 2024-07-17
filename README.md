# Projects
### README

Este repositório contém um exemplo de aplicação de classificação binária utilizando aprendizado supervisionado com Python e bibliotecas como Pandas e Scikit-Learn.

#### Descrição do Projeto

O código apresentado aqui visa construir e avaliar um modelo de classificação binária para prever se projetos foram concluídos ou não com base em características como horas esperadas e preço estimado. Os dados foram carregados de um arquivo CSV disponível online.

#### Pré-requisitos

Para executar o código, é necessário ter instalado:
- Python 
- Bibliotecas: pandas, scikit-learn

#### Instalação

1. Clone o repositório:
   ```
   git clone <URL_do_repositório>
   ```

2. Instale as dependências:
   ```
   pip install pandas scikit-learn
   ```

#### Como Utilizar

1. Importe as bibliotecas necessárias:
   ```python
   import pandas as pd
   from sklearn.svm import LinearSVC
   from sklearn.metrics import accuracy_score
   from sklearn.model_selection import train_test_split
   from sklearn.dummy import DummyClassifier
   ```

2. Carregue os dados do CSV a partir de uma URL:
   ```python
   url = "https://raw.githubusercontent.com/paolasouza/data_mining_and_big_data/ec70f701a784820fa6ca326c0d51d8740028da03/projects.csv"
   dados = pd.read_csv(url)
   ```

3. Prepare os dados renomeando colunas se necessário:
   ```python
   x = dados[["unfinished", "expected_hours", "price"]]  # features
   y = dados["unfinished"]  # classes
   ```

4. Divida os dados em conjuntos de treino e teste:
   ```python
   seed = 20  # pode ser qualquer valor fixo
   treino_x, teste_x, treino_y, teste_y = train_test_split(x, y, random_state=seed, test_size=0.25, stratify=y)
   print("Treinamento com %d elementos e testaremos com %d elementos" % (len(treino_x), len(teste_x)))
   ```

5. Crie um modelo de classificação (exemplo com LinearSVC):
   ```python
   modelo = LinearSVC()
   modelo.fit(treino_x, treino_y)
   ```

6. Avalie a acurácia do modelo:
   ```python
   previsoes = modelo.predict(teste_x)
   acuracia = accuracy_score(teste_y, previsoes) * 100
   acuracia_model_score = modelo.score(teste_x, teste_y) * 100
   print("A acurácia foi %.2f%%" % acuracia)
   print("A acurácia foi %.2f%%" % acuracia_model_score)
   ```

7. Compare com um baseline (Dummy Classifier):
   ```python
   dummy_stratified = DummyClassifier()
   dummy_stratified.fit(treino_x, treino_y)
   acuracia_dummy = dummy_stratified.score(teste_x, teste_y) * 100
   print("A acurácia do dummy stratified foi %.2f%%" % acuracia_dummy)
   ```

#### Resultados Esperados

Os resultados esperados incluem a acurácia do modelo treinado e a acurácia de um baseline para comparação. O modelo utiliza características dos projetos para prever se eles foram concluídos com sucesso.

#### Contribuições

Contribuições são bem-vindas! Caso queira melhorar este código, sinta-se à vontade para criar um fork do repositório e enviar um pull request com suas alterações.


#### Autores

Desenvolvido por Lorran Luciano Oliveira Mendes

---

