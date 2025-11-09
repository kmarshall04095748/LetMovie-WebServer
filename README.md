# 🎬 LetMovie - Web Server

**LetMovie** é um projeto de web server full-stack que utiliza **Python puro** (`http.server`) para o backend e um frontend de **HTML, CSS e JavaScript** para o cliente.  
O sistema permite **cadastrar, listar e excluir filmes** de um banco de dados **MySQL**.

Este projeto foi construído **sem o uso de frameworks de backend** (como Flask ou Django) para focar nos fundamentos do protocolo HTTP e na manipulação de requisições.

---

## ✨ Funcionalidades

### 🧠 Backend 100% Python Nativo
O servidor é construído usando apenas as bibliotecas padrão:
- `http.server`
- `json`
- `os`
- `re`

### 🌐 Servidor de API RESTful
- **GET `/api/filmes`** → Lista todos os filmes do banco com dados agregados (atores, diretores, etc.).
- **GET `/api/filme/{id}`** → Retorna os detalhes de um filme específico (usado na tela de sucesso).
- **POST `/cadastro`** → Adiciona um novo filme ao banco de dados.
- **POST `/delete`** → Exclui um filme existente (lidando com chaves estrangeiras).

### 🗂️ Servidor de Arquivos Estáticos
Serve os arquivos `html/`, `css/` e `js/` diretamente para o navegador.

### ✅ Validação de Backend
- Verifica se todos os campos obrigatórios foram preenchidos.
- Impede a inserção de filmes com **títulos duplicados**.

### ⚙️ Frontend Dinâmico
O **JavaScript** (via `fetch API`) se comunica com o backend para listar, cadastrar e excluir filmes **sem recarregar a página**.

---

## 🛠️ Tecnologias Utilizadas

| Camada | Tecnologia |
|---------|-------------|
| **Backend** | Python 3 (`http.server`) |
| **Database** | MySQL |
| **Conector Python-MySQL** | `mysql-connector-python` |
| **Frontend** | HTML5, CSS3, JavaScript (ES6+) |

---

## 📁 Estrutura do Projeto

WEB-SERVER/
├── bd/
│ └── webserver.sql # Script de criação do banco
├── css/
│ └── style.css # Estilos
├── html/
│ ├── cadastro.html # Página de cadastro
│ ├── index.html # Página inicial
│ ├── listar_filmes.html # Página de listagem
│ ├── login.html # Página de login (não funcional)
│ └── sucesso.html # Página de sucesso pós-cadastro
├── img/
│ └── wallpaper-netflix.jpg
├── js/
│ └── script.js # Lógica do frontend
└── server/
└── server.py # Servidor backend

yaml
Copiar código

---

## 🚀 Instalação e Execução

Siga estes passos para configurar e executar o projeto localmente.

### 1️⃣ Pré-requisitos
- **Python 3.x** instalado  
- **MySQL Server** instalado e em execução  

---

### 2️⃣ Configuração do Banco de Dados

Abra seu cliente MySQL (Workbench, terminal, etc.) e execute:

```sql
CREATE DATABASE LetMovie;
USE LetMovie;
Depois, rode o script bd/webserver.sql para criar todas as tabelas e popular o banco com dados iniciais.

3️⃣ Instalação das Dependências
O projeto tem apenas uma dependência Python.
No terminal, instale-a com:

bash
Copiar código
pip install mysql-connector-python
4️⃣ Configuração do Servidor
Abra o arquivo server/server.py e verifique se as credenciais estão corretas:

python
Copiar código
try:
    mydb = mysql.connector.connect(
        host="localhost",
        user="root",
        password="root",  # <-- MUDE AQUI SE NECESSÁRIO
        database="LetMovie"
    )
5️⃣ Executando o Servidor
No terminal, dentro da pasta raiz do projeto (WEB-SERVER/), execute:

bash
Copiar código
python server/server.py
Se você usa Python 3 em paralelo, use:

bash
Copiar código
python3 server/server.py
Você verá a mensagem:

arduino
Copiar código
🚀 Servidor rodando em http://localhost:8000
Servindo arquivos do diretório: C:\Caminho\Para\WEB-SERVER
🖥️ Como Usar
Com o servidor rodando, abra seu navegador e acesse:
👉 http://localhost:8000

A página inicial (index.html) será carregada.

Você pode:

Navegar até "Adicionar Filmes" para cadastrar um novo filme.

Ir até "Filmes" para listar e excluir filmes existentes.
