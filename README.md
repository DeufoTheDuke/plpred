# plpred

By Woloski

A protein subcellular location preditction program

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
- `preprocessing.py`: Executa as funções de preprocessamento nos arquivos dentro da pasta Data/Raw, transformando elas em um DataFrame
- `plpred`: Diretório principal do pacote, com sa funções da aplicação.