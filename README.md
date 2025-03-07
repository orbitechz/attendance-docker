# Sistema de Controle de Presença

Este repositório contém um sistema de controle de presença composto por um frontend, backend e banco de dados PostgreSQL, todos executados em contêineres Docker.

## Pré-requisitos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Configuração

### 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd <nome-da-pasta>
```

### 2. Configure o arquivo de variáveis de ambiente

Copie o arquivo `.env.example` para criar um novo arquivo chamado `.env`:

```bash
cp .env.example .env
```

Edite o arquivo `.env` com as seguintes configurações recomendadas:

```
DB_HOST=postgres
DB_PORT=5432
DB_NOME=attendance
DB_USER=postgres
DB_PWD=postgres
DDL=create
JWT_SECRET="sua-chave-secreta-aqui"
REACT_APP_API_URL=/api
API_HOST=attendance-backend
API_PORT=8080
```

### Detalhes das variáveis:


- `DB_HOST`: Nome do contêiner do banco de dados (postgres)
- `DB_PORT`: Porta do PostgreSQL (5432)
- `DB_NOME`: Nome do banco de dados
- `DB_USER`: Usuário do banco de dados
- `DB_PWD`: Senha do banco de dados
- `DDL`: Opção de inicialização do banco de dados
    - `create-drop`: Cria e exclui o esquema ao finalizar
    - `create`: Cria o esquema
    - `update`: Atualiza o esquema
    - `validate`: Valida o esquema
- `JWT_SECRET`: Chave secreta para assinatura de tokens JWT
- `REACT_APP_API_URL`: URL de proxy reverso para o backend
- `API_HOST`: Nome do contêiner do backend
- `API_PORT`: Porta do backend

### 3. Iniciar os contêineres

```bash
docker compose up -d
```

Este comando iniciará três contêineres:

- PostgreSQL (banco de dados)
- Backend da aplicação
- Frontend da aplicação

## Acessando o sistema

- Frontend: http://localhost
- Backend API: http://localhost:8080 ou http://localhost/attendance-api (via proxy reverso)
- Banco de dados: localhost:5432

## Estrutura do projeto

- `docker-compose.yml`: Configuração dos serviços Docker
- `.env`: Variáveis de ambiente (não incluído no repositório)
- `db-data`: Diretório onde os dados do PostgreSQL são armazenados (persistência)

## Parando os contêineres

```bash
docker compose down
```

Para remover os volumes e iniciar do zero:

```bash
docker compose down -v
```

**Nota**: Isso excluirá todos os dados do banco de dados!