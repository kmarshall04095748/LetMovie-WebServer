# 🎬 LetMovie - Web Server

![Python](https://img.shields.io/badge/Python-3.x-blue.svg) ![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg) ![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

LetMovie é um projeto de web server full-stack que utiliza **Python puro** (módulo `http.server`) para o backend e um frontend de **HTML, CSS e JavaScript** para o cliente. O sistema permite cadastrar, listar e excluir filmes de um banco de dados MySQL.

Este projeto foi construído sem o uso de frameworks de backend (como Flask ou Django) para focar nos fundamentos do protocolo HTTP e na manipulação de requisições.

## ✨ Funcionalidades

* **Backend 100% Python Nativo:** O servidor é construído usando apenas as bibliotecas padrão `http.server`, `json`, `os` e `re`.
* **Servidor de API RESTful:**
    * `GET /api/filmes`: Lista todos os filmes do banco com dados agregados (atores, diretores, etc.).
    * `GET /api/filme/{id}`: Retorna os detalhes de um filme específico (usado na tela de sucesso).
    * `POST /cadastro`: Adiciona um novo filme ao banco de dados.
    * `POST /delete`: Exclui um filme existente (lidando com chaves estrangeiras).
* **Servidor de Arquivos Estáticos:** Serve os arquivos `html/`, `css/` e `js/` para o navegador.
* **Validação de Backend:**
    * Verifica se todos os campos obrigatórios foram preenchidos.
    * Impede a inserção de filmes com títulos duplicados.
* **Frontend Dinâmico:** O JavaScript (via `fetch API`) se comunica com o backend para listar, cadastrar e excluir filmes sem recarregar a página.

---

## 🛠️ Tecnologias Utilizadas

* **Backend:** Python 3 (`http.server`)
* **Database:** MySQL
* **Conector Python-MySQL:** `mysql-connector-python`
* **Frontend:** HTML5, CSS3, JavaScript (ES6+)

---

## 📁 Estrutura do Projeto
```
WEB-SERVER/
├── bd/
│   └── webserver.sql         # Script de criação do banco
├── css/
│   └── style.css             # Estilos gerais
├── html/
│   ├── cadastro.html         # Página de cadastro de filmes
│   ├── index.html            # Página inicial
│   ├── listar_filmes.html    # Página de listagem
│   ├── login.html            # Página de login (não funcional)
│   └── sucesso.html          # Tela de sucesso pós-cadastro
├── img/
│   └── wallpaper-netflix.jpg # Imagem de fundo
├── js/
│   └── script.js             # Lógica do frontend
└── server/
    └── server.py             # Servidor backend
```

---

## 🚀 Instalação e Execução

Siga estes passos para configurar e executar o projeto localmente.

### 1. Pré-requisitos

* **Python 3.x** instalado.
* **MySQL Server** instalado e em execução.

### 2. Configuração do Banco de Dados

1.  Abra seu cliente MySQL (Workbench, terminal, etc.).
2.  Crie o banco de dados:
    ```sql
    CREATE DATABASE LetMovie;
    ```
3.  Use o banco recém-criado:
    ```sql
    USE LetMovie;
    ```
4.  Execute todo o script do arquivo `bd/webserver.sql` (código incluído abaixo) para criar todas as tabelas e popular o banco com dados iniciais.

### 3. Instalação das Dependências

O projeto tem apenas uma dependência Python. No seu terminal, instale-a:


pip install mysql-connector-python

### 4. Configuração do Servidor
Abra o arquivo `server/server.py` (código incluído abaixo).
Na seção `Conexão com o Banco de Dados`, verifique se o `host`, `user` e, principalmente, a `password` estão corretos para a sua instalação do MySQL.

```
python
try:
    mydb = mysql.connector.connect(
        host="localhost",
        user="root",
        password="root",  # <-- MUDE AQUI SE NECESSÁRIO
        database="LetMovie"
    )
```

### 4. Configuração do Servidor

Abra o arquivo server/server.py e verifique a seção de conexão com o banco de dados.
Certifique-se de que host, user e password estão corretos conforme sua instalação:

```
try:
    mydb = mysql.connector.connect(
        host="localhost",
        user="root",
        password="root",  # <-- Altere aqui se necessário
        database="LetMovie"
    )
```

5. Executando o Servidor

- No terminal, acesse a pasta raiz do projeto (WEB-SERVER) e execute:
- python server/server.py


- 💡 Caso utilize Python 3 em paralelo, use python3 em vez de python.
Ao iniciar com sucesso, você verá mensagens como:

🚀 Servidor rodando em http://localhost:8000
Servindo arquivos do diretório: C:\Caminho\Para\WEB-SERVER

## 🖥️ Como Usar

- Acesse no navegador: 👉 http://localhost:8000
- A página inicial (index.html) será exibida.
- Clique em "Adicionar Filmes" para abrir o formulário de cadastro.
- Após cadastrar, você será redirecionado para a tela de sucesso, onde poderá visualizar os detalhes do novo filme.

## 📄 Licença

Este projeto está licenciado sob a MIT License.
Consulte o arquivo LICENSE para mais informações.

## 💡 Observação Final

Este projeto foi desenvolvido com o objetivo de compreender profundamente o funcionamento de um servidor HTTP em Python e a comunicação entre frontend e backend sem o uso de frameworks.
Uma base sólida para quem deseja dominar o desenvolvimento full-stack com fundamentos puros.
