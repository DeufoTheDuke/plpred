# plpred

By Woloski

A protein subcellular location preditction program

Available at [https://rw-plpred.herokuapp.com/] (https://rw-plpred.herokuapp.com/)

## Setup

```
$ make setup
```

## Estrutura do Projeto

- `enviroment.yml`: Arquivo ede estruturação e configuração do ambiente. Descreve quais serão os programas que serão instalados (ou seja, as dependências do projeto), o nome do ambiente, onde buscar os programas, etc.
- `requirements.txt`: Lista de bibliotecas/pacotes que serão instalados no ambiente atual.
- `MakeFile`: Cria regras para simplificar a execução de comandos mais longos.
- `Data/Raw`: Contem arquivos .fasta com sequências de aminoácidos de proteínas de Membrana e Citoplasmáticas
- `Data/Processed`: Contem um arquivo processed.csv com as proteínas dos arquivos .fasta processadas em um DataFrame de acordo com a porcentagem da sua composição de aminoácidos, assim como um label dizendo se a proteína é de membrana ou não.
- `Data/Models`: Contem os modelos treinados serializados utilizando o pacote Pickle
- `preprocessing.py`: Executa as funções de preprocessamento nos arquivos dentro da pasta Data/Raw, transformando elas em um DataFrame
- `plpred`: Diretório principal do pacote, com sa funções da aplicação.
- `plpred/models`: Disponibiliza modelos de treinamento baseados em *Random Forest*, *Gradient Boost*, SVM e Redes Neurais (NN)
- `tests`: Conjunto de testes unitários para os componentes do Plpred.

## Command Line Interface (CLI)

### `plpred-preprocess`
```
usage: plpred-preprocess [-h] -m MEMBRANE_PROTEINS -c CYTOPLASM_PROTEINS -o OUTPUT

plpred-preprocessing: pre-process data to use in training

optional arguments:
  -h, --help            show this help message and exit
  -m MEMBRANE_PROTEINS, --membrane_proteins MEMBRANE_PROTEINS
                        Path to the file containing membrane proteins (.fasta)
  -c CYTOPLASM_PROTEINS, --cytoplasm_proteins CYTOPLASM_PROTEINS
                        Path to the file containing cytoplasm proteins (.fasta)
  -o OUTPUT, --output OUTPUT
                        Path to the output file (.csv)
```
### `plpred-train`
```
usage: plpred-train [-h] -p PROCESSED_DATASET -o OUTPUT [-r]
                    [-a {random_forest,neural_network,gradient_boosting,svm}]

plpred-train: model training tool

optional arguments:
  -h, --help            show this help message and exit
  -p PROCESSED_DATASET, --processed_dataset PROCESSED_DATASET
                        Processed dataset generated by plpred-preprocessing (.csv)
  -o OUTPUT, --output OUTPUT
                        Path to the output trained model (.pickle)
  -r, --report          Show classification report
  -a {random_forest,neural_network,gradient_boosting,svm}, --algorithm {random_forest,neural_network,gradient_boosting,svm}
                        Machine learning algorithm
```
### `plpred-predict`
```
usage: plpred-predict [-h] -i INPUT -o OUTPUT -m MODEL

plpred-predict: Membrane protein prediction tool

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT, --input INPUT
                        Input file (.fasta)
  -o OUTPUT, --output OUTPUT
                        Output file (.csv)
  -m MODEL, --model MODEL
                        Trained model (.pickle)
```

### `plpred-server`
```
usage: plpred-server [-h] -H HOST -p PORT -m MODEL

plpred-server:subcellular location prediction server

optional arguments:
  -h, --help            show this help message and exit
  -H HOST, --host HOST  host address
  -p PORT, --port PORT  host port
  -m MODEL, --model MODEL
                        trained model to be deployed
```