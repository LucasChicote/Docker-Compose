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


# Vídeo mostando comandos antes da contanerização e depois no docker
[![Vídeo de Demonstração](https://img.youtube.com/vi/LBQA38ktVek/hqdefault.jpg)](https://youtu.be/LBQA38ktVek?si=6meULpGIF0Ib51Qt)

## Estrutura do Pojeto

```bash
CP_DockerCompose
│
├── app.py
├── requirements.txt
├── Dockerfile
└── docker-compose.yml
```

## Dockerfile

O Dockerfile é responsável por cirar a imagem da aplicação

Principais etapas:
* definição da imagem base Python
* instalaçõa das dependèncias
* cópia da aplicação
* execução da API

## docker-compose.yml

O Docker Compose define dois serviços:

##dp

Container do banco de dados MySQL

##API

Container da aplicação Flask

Também são configurados:
* rede interna
* volume para persitência
* healthcheck
* variáveis de ambiente

# Comandos Essenciais do Docker Compose

Subir containers:
```bash
docker comppse up
```
Subir container em background:
```bash
docker compose up -d
```
Ver containers ativos:
```bash
docker ps
```
Parar containers:
```bash
docker compose down
```
Rebuild das imagens:
```bash
docker compose up --build
```
Ver logs:
```bash
docker compose logs
```
Ver logs de um container específico
```bash
docker compose logs api
```

# Troubleshooting (Problemas comuns)

Erro: container já existe

Erro:
```bash
Conflict. The container name is already in use
```
Solução:
```bash
docker rm -f nome_container
```
# Conclusão

Com Docker Compose foi possível:
* padronizar o ambiente
* facilitar o deploy
* separar aplicação e banco
* garantir portabilidade

A aplicação pode ser executada com apenas um comando, simplificando o processo de desenvolvimento e implantação.


   



