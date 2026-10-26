# Sistema de Gestão de Estoque (SGE)

O **Sistema de Gestão de Estoque (SGE)** é uma aplicação web desenvolvida com Python, Django e Bootstrap 5, voltada ao gerenciamento de produtos e ao controle de movimentações de estoque.

O projeto reúne funcionalidades para cadastro de produtos, marcas, categorias e fornecedores, além do registro de entradas e saídas. Também possui autenticação de usuários, controle de permissões e um dashboard com indicadores para acompanhamento das operações.

## Funcionalidades

- **Produtos:** cadastro, consulta, edição e exclusão de produtos.
- **Marcas e categorias:** organização e gerenciamento dos produtos cadastrados.
- **Fornecedores:** cadastro e gerenciamento de fornecedores.
- **Entradas de estoque:** registro de mercadorias recebidas.
- **Saídas de estoque:** controle das movimentações de saída.
- **Dashboard:** visualização de indicadores e gráficos de estoque e vendas.
- **Autenticação:** acesso ao sistema por meio de login.
- **Permissões:** controle de acesso às funcionalidades conforme as permissões de cada usuário.
- **API REST:** endpoints para integração e manipulação de dados.

## Tecnologias utilizadas

- Python
- Django 6.1.2
- Django REST Framework
- Simple JWT
- Bootstrap 5
- HTML e CSS
- JavaScript
- Chart.js

## Pré-requisitos

Antes de executar o projeto, certifique-se de ter instalado:

- Python compatível com Django 6.1
- Git
- Pip

As bibliotecas necessárias estão disponíveis no arquivo `requirements.txt`.

## Instalação e configuração

### 1. Clonar o repositório

```bash
git clone https://github.com/rimarassi/sge.git
```

Acesse o diretório do projeto:

```bash
cd sge
```

### 2. Criar e ativar o ambiente virtual

Crie um ambiente virtual:

```bash
python -m venv venv
```

Ative o ambiente virtual no Windows:

```powershell
.\venv\Scripts\Activate.ps1
```

### 3. Instalar as dependências

Com o ambiente virtual ativado, execute:

```bash
pip install -r requirements.txt
```

Para instalar também as dependências de desenvolvimento, consulte o arquivo `requirements_dev.txt`.

### 4. Configurar o banco de dados

Execute as migrações para criar as tabelas necessárias:

```bash
python manage.py migrate
```

### 5. Criar um superusuário

Para gerenciar usuários e permissões pelo painel administrativo do Django, execute:

```bash
python manage.py createsuperuser
```

Informe o nome de usuário, e-mail (opcional) e senha solicitados no terminal.

### 6. Executar o projeto

Inicie o servidor de desenvolvimento:

```bash
python manage.py runserver
```

Após a inicialização, o sistema estará disponível em:

**Aplicação:** http://127.0.0.1:8000/

**Painel administrativo:** http://127.0.0.1:8000/admin/

## Autenticação e permissões

O SGE utiliza o sistema de autenticação do Django para controlar o acesso dos usuários.

As permissões podem ser configuradas pelo administrador, permitindo definir quais usuários poderão visualizar, cadastrar, editar ou excluir registros.

A aplicação também possui uma estrutura de autenticação para utilização com a API.

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
├── manage.py
├── requirements.txt
└── requirements_dev.txt
```

## Objetivo do projeto

O SGE foi desenvolvido com o objetivo de aprimorar conhecimentos em desenvolvimento web utilizando Python e Django.

Durante o desenvolvimento, foram aplicados conceitos de operações CRUD, relacionamento entre modelos, autenticação, gerenciamento de permissões, APIs REST e construção de interfaces web.

O projeto também serve como prática para a organização de aplicações Django em módulos independentes.
