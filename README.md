# Desafio Empregados Auth

Projeto desenvolvido como solução do desafio **Empregados Auth** da DevSuperior, com foco em autenticação, autorização, validação de dados e controle de acesso utilizando Spring Security e OAuth2.

## 📋 Sobre o Projeto

O sistema gerencia funcionários (*Employees*) e departamentos (*Departments*), possuindo uma relação **N:1**, onde vários funcionários podem pertencer a um único departamento.

Além do CRUD de funcionários, o projeto implementa mecanismos de segurança baseados em perfis de usuário, garantindo diferentes níveis de acesso aos recursos da aplicação.

---

## 🚀 Tecnologias Utilizadas

- Java 17+
- Spring Boot
- Spring Data JPA
- Spring Security
- OAuth2
- Bean Validation
- H2 Database (ambiente de desenvolvimento)
- Maven

---

## 📊 Modelo de Domínio

### Employee
- id
- name
- email
- department

### Department
- id
- name

### User
- id
- username
- password
- roles

### Role
- id
- authority

---

## 🔐 Controle de Acesso

Todas as rotas da aplicação são protegidas.

### Perfil ADMIN
Possui acesso total aos recursos:

- Consultar funcionários e departamentos
- Criar funcionários
- Atualizar funcionários
- Remover funcionários

### Perfil OPERATOR
Possui acesso somente de leitura:

- Consultar funcionários
- Consultar departamentos

---

## ✅ Validações

As seguintes validações foram implementadas para a entidade Employee:

| Campo | Regra |
|---------|---------|
| name | Não pode ser vazio |
| email | Deve possuir formato válido |
| department | Não pode ser nulo |

As validações são realizadas utilizando **Bean Validation**.

---

## ⚠️ Tratamento de Exceções

Foi implementada uma infraestrutura global para tratamento de erros contendo:

- Exceções customizadas de serviço
- Respostas padronizadas para erros
- Manipulação centralizada através de `ControllerAdvice`

Exemplos:

- Recurso não encontrado
- Violação de validação
- Acesso negado
- Erros de autenticação

---

## 🔑 Segurança

A aplicação utiliza Spring Security com OAuth2 para autenticação e autorização.

### Implementações

- Configuração do Authorization Server
- Configuração do Resource Server
- Password Grant customizado
- Controle de acesso baseado em Roles
- Rotas protegidas
- Integração com banco de dados para autenticação

---

## 📂 Estrutura do Projeto

```text
src
├── main
│   ├── java
│   │   ├── config
│   │   ├── controllers
│   │   ├── dto
│   │   ├── entities
│   │   ├── repositories
│   │   ├── services
│   │   ├── security
│   │   └── exceptions
│   └── resources
│       ├── application.properties
│       └── import.sql
└── test
```

## ▶️ Como Executar

Pré-requisitos
Java 17 ou superior
Maven 3.8+

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/desafio-empregados-auth.git
