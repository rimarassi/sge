# Sistema de Gestão de Estoque (SGE)

O **Sistema de Gestão de Estoque (SGE)** é uma aplicação web desenvolvida com Python e Django, com interface construída utilizando Bootstrap 5. O sistema permite gerenciar produtos e acompanhar movimentações de estoque em um único lugar.

O projeto utiliza **Docker Compose** para executar a aplicação Django e o banco de dados **PostgreSQL** em serviços separados, facilitando a configuração do ambiente.

## Funcionalidades

- **Produtos:** cadastro, consulta, edição e exclusão de produtos.
- **Marcas e categorias:** organização dos produtos cadastrados.
- **Fornecedores:** cadastro e gerenciamento de fornecedores.
- **Entradas de estoque:** registro de mercadorias recebidas.
- **Saídas de estoque:** controle das movimentações de saída.
- **Dashboard:** indicadores e gráficos relacionados ao estoque e às vendas.
- **Autenticação e permissões:** controle de acesso dos usuários.
- **API REST:** endpoints para integração e manipulação de dados.

## Tecnologias utilizadas

- Python 3.14
- Django 6.1
- Django REST Framework
- Simple JWT
- PostgreSQL 18
- Docker e Docker Compose
- Bootstrap 5, HTML e CSS
- JavaScript e Chart.js

## Pré-requisitos

Para executar a versão conteinerizada, instale:

- [Git](https://git-scm.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (inclui Docker Compose)

## Como executar com Docker

### 1. Clonar o repositório

```bash
git clone https://github.com/rimarassi/sge.git
cd sge
```

### 2. Configurar as variáveis de ambiente

Na raiz do projeto, crie um arquivo chamado `.env`, no mesmo diretório do `docker-compose.yml`, com as variáveis abaixo:

```dotenv
ENVIRONMENT=prd
POSTGRES_DB=sge
POSTGRES_USER=postgres
POSTGRES_PASSWORD=defina_uma_senha_local
POSTGRES_HOST=sge_db
POSTGRES_PORT=5432
```

Substitua `defina_uma_senha_local` por uma senha de sua escolha. O arquivo `.env` contém configurações locais e não deve ser enviado ao GitHub.

### 3. Construir e iniciar os serviços

Com o Docker Desktop em execução, execute:

```bash
docker compose up --build -d
```

O Compose inicia dois serviços:

- `sge_web`: aplicação Django, disponível na porta `8000`.
- `sge_db`: banco de dados PostgreSQL, disponível na porta `5432` para conexões a partir do computador host.

O Dockerfile executa as migrações do Django ao iniciar a aplicação.

### 4. Criar um usuário administrador

```bash
docker compose exec sge_web python manage.py createsuperuser
```

Siga as instruções no terminal para definir o usuário e a senha.

### 5. Acessar o sistema

- **Aplicação:** [http://localhost:8000/](http://localhost:8000/)
- **Painel administrativo:** [http://localhost:8000/admin/](http://localhost:8000/admin/)

### Comandos úteis do Docker Compose

Ver os serviços em execução:

```bash
docker compose ps
```

Acompanhar os logs da aplicação:

```bash
docker compose logs -f sge_web
```

Parar os serviços sem excluir os dados do banco:

```bash
docker compose down
```

Iniciar novamente os serviços:

```bash
docker compose up -d
```

Os dados do PostgreSQL são armazenados no volume nomeado `postgres_data`, para persistirem quando os contêineres forem recriados. **Evite usar `docker compose down -v` se quiser preservar os dados**, pois esse comando também remove os volumes declarados pelo Compose.

## Executar localmente sem Docker (opcional)

A configuração de desenvolvimento também pode usar SQLite, conforme a variável `ENVIRONMENT` definida nas configurações do Django.

1. Crie e ative um ambiente virtual:

   ```powershell
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   ```

2. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

3. Execute as migrações:

   ```bash
   python manage.py migrate
   ```

4. Crie um administrador, se necessário:

   ```bash
   python manage.py createsuperuser
   ```

5. Inicie o servidor:

   ```bash
   python manage.py runserver
   ```

Acesse [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

## Estrutura do projeto

```text
sge/
├── app/                  # Configurações e aplicação principal
├── authentication/       # Autenticação
├── brands/               # Marcas
├── categories/           # Categorias
├── inflows/              # Entradas de estoque
├── outflows/             # Saídas de estoque
├── products/             # Produtos
├── suppliers/            # Fornecedores
├── Dockerfile             # Imagem da aplicação Django
├── docker-compose.yml     # Serviços Django e PostgreSQL
├── .dockerignore          # Arquivos ignorados no build
├── requirements.txt       # Dependências da aplicação
├── requirements_dev.txt   # Dependências de desenvolvimento
└── manage.py
```

## Objetivo do projeto

O SGE foi desenvolvido para praticar desenvolvimento web com Python e Django, incluindo operações CRUD, relacionamento entre modelos, autenticação, permissões, APIs REST e construção de interfaces web. A configuração com Docker Compose e PostgreSQL também permite praticar a conteinerização e a integração da aplicação com um banco de dados relacional.
