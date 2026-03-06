# BattleRank API com Docker Compose
## Descrição do Projeto

O BattleRank API é uma aplicação simples desenvolvida em Python (Flask) com MySQL que permite registrar jogadores e suas pontuações em um ranking.

A API implementa operações de CRUD (Create, Read, Update, Delete) para manipular os dados no banco.

O projeto foi posteriormente containerizado utilizando Docker e Docker Compose, permitindo executar toda a aplicação com apenas um comando.

## Arquitetura
A aplicação é composta por dois serviços principais:

## API

* Desenvolvida em Python + Flask 
* Responsável pelas requisições HTTP
* Realiza operações CRUD no banco

## Banco de Dados
* MySQL 8.4
* Armazena os dados dos jogadores e pontuações

## Tecnologias utilizadas

* Python 3.1.1
* Flask
* MySQL 8.4
* Docker
* Dokcer Compose

  
## Instruções de uso

1. Clonar o projeto
```bash
git clone https://github.com/LucasChicote/Dokcer-compose.git
```
1.1 Entrar na pasta do projeto
```bash
cd CP_DockerCompose
```
## Executando o projeto SEM containerização
Antes da containerização, a aplicação era executada localmente.

Executar a aplicação
```bash
python app.py
```
A API ficará disponível em:
```bash
http://localhost:5000
```
Exemplo de endpoit
```bash
http://localhost:5000/leaderboard
```
## Executando com Docker Compose
O Docker Compose permite subir todos os serviços automaticamente.

Subir os containers
```bash
docker compose up -d
```
Este comando:
* cria a rede
* cria os containers
* cria os volumes
* inicia os serviços

## Verificar containers em execução
```bash
docker ps
```
Exemplo de saida:
```bash
CONTAINER ID   IMAGE                  PORTS
battlerank_api cp_dockercompose-api   5000
battlerank_db  mysql:8.4              3306
```

## Testando a API
A API pode ser acessada no navegador:
```bash
http://localhost:5000/leaderboard
```
Exemplo de resposta:
```bash
[
  {
    "id": 2,
    "nome": "Kratos",
    "pontuacao": 2000
  },
  {
    "id": 3,
    "nome": "Spider",
    "pontuacao": 1500
  },
  {
    "id": 1,
    "nome": "Lucas",
    "pontuacao": 1000
  }
]
```

## Crud

1. CREATE
```bash
IUSE battlerank;

INSERT INTO players (nome,pontuacao)
VALUES ('Mario',1800);
```
2. READ
```bash
SELECT * FROM players;
```
3. UPDATE
```bash
UPDATE players
SET pontuacao = 2500
WHERE nome = 'Mario';
```
4. DELETE
```bash
DELETE FROM players
WHERE nome = 'Mario';
```
Para sair do MySQL:
```bash
exit
```
## Para parar um container
usa-se:
```bash
docker-compose down
```
Este comando:
* Remove os containers
* Para de rodar a aplicação


# Vídeo demonstrativo do CRUD
[![Vídeo de Demonstração da Sprint 2](https://img.youtube.com/vi/zdbPgIbVH-s/hqdefault.jpg)](https://youtu.be/zdbPgIbVH-s?si=DIloXwdbeYgNG8x4)

# Subindo arquivo de Java pra BackEnd

## Deployments para subir Java na VM AZURE

1. Entrar na sua VM (após colocar a senha)
```bash
ssh BackEnd@51.107.0.17
```
2. Atualizar pacotes
```bash
sudo apt update
```
3. Instalação do docker
```bash
sudo apt install git docker.io -y
```
4. Adicionar usuário ao grupo
```bash
sudo usermod -aG docker ${USER}
```
5. Clonando projeto
```bash
git clone https://github.com/AlexisRondo/mentalcheck-backend.git
```
6. Entrando no diretório do projeto
```bash
cd mentalcheck/
```
7. Compilar projeto e criar imagem Docker
```bash
docker build -t lumejava-api .
```
8. Rodar container
```bash
docker run -d -p 8080:8080 --name mentalcheck-backend --restart always mentalcheckjava-api
```
## Vídeo demonstrativo
[![Vídeo de Demonstração da Sprint 2](https://img.youtube.com/vi/JyoUbbqZLTk/hqdefault.jpg)](https://youtu.be/JyoUbbqZLTk?si=CJScPbS657rdl9nO)




   



