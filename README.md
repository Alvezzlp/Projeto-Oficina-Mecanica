# ⚙️ AutoMecânica Pro - Sistema Integrado de Gestão de Oficina (SAEP)

> Sistema web full-stack para gestão operacional de oficina mecânica, cadastro de clientes e veículos, além de agendamento de serviços com conformidade à LGPD e regras de negócio do edital SAEP / SENAI.

---

## 📌 Sobre o Projeto

O **AutoMecânica Pro** foi desenvolvido para solucionar problemas operacionais comuns em oficinas mecânicas, como descontrole de agendamentos, duplicidade de cadastros e falta de conformidade no tratamento de dados pessoais. 

A aplicação realiza a gestão completa de clientes, frota de veículos e serviços agendados, contando com autenticação segura, controle de expiração de sessão e criptografia de dados sensíveis.

---

## 🛠️ Tecnologias Utilizadas

### **Backend**
* **Python 3.10+** / **Flask 3.0.3** (Microframework web)
* **MySQL 8.0** (Banco de dados relacional com engine InnoDB)
* **mysql-connector-python 8.4.0** (Driver oficial de conexão)
* **Bcrypt 4.1.3** (Hashing seguro para senhas e conformidade com LGPD)
* **Werkzeug 3.0.3** (Utilitários WSGI)

### **Frontend**
* **HTML5** (Semântico)
* **CSS3** (Estilização pura e responsiva)
* **JavaScript (Vanilla JS)** (Manipulação dinâmica de modais sem frameworks pesados)

---

## 🔐 Segurança & LGPD

* **Proteção de Dados Pessoais (LGPD):** O CPF dos clientes é validado (exatamente 11 dígitos) e armazenado no banco de dados utilizando criptografia unidirecional com salt dinâmico (`Bcrypt`).
* **Autenticação Segura:** Senhas criptografadas com `Bcrypt`. Feedback explícito em caso de credenciais inválidas.
* **Controle de Sessão:** Sessões temporárias com expiração automática após 15 minutos de inatividade (`PERMANENT_SESSION_LIFETIME = 15 min`).

---

## 📁 Estrutura do Projeto

```text
oficina_mecanica/
├── saep_db.sql               # Script SQL (Criação de DB, tabelas e carga inicial)
├── .gitignore                # Arquivos ignorados pelo Git
├── README.md                 # Documentação do repositório
└── sistema/
    ├── app.py                # Servidor principal e inicialização da aplicação
    ├── banco.py              # Módulo de conexão com o banco MySQL
    ├── autenticacao.py       # Lógica de login, logout e controle de acesso
    ├── clientes.py           # CRUD de clientes e hashing de CPF
    ├── veiculos.py           # CRUD de veículos vinculado ao cliente
    ├── agendamento.py        # Gestão e ordenação de agendamentos
    ├── rotas.py              # Controlador central de rotas e interceptores
    ├── requirements.txt      # Dependências do projeto Python
    ├── static/
    │   ├── css/
    │   │   └── style.css     # Estilos da aplicação
    │   └── js/
    │       └── main.js       # Scripts para manipulação de modais
    └── templates/            # Views HTML (Jinja2)
        ├── base.html
        ├── login.html
        ├── dashboard.html
        ├── clientes.html
        ├── veiculos.html
        └── agendamentos.html
