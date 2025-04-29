# Projeto NestJS com Prisma e SQLite: Autenticação e CRUD de Usuários

## 📋 Visão Geral

Este projeto é uma API RESTful construída com NestJS que oferece um sistema completo de autenticação e operações CRUD para usuários. Utiliza Prisma como ORM e SQLite como banco de dados, sendo uma solução eficiente para aplicações que necessitam de gerenciamento de usuários com autenticação segura.

## ✨ Funcionalidades

- **Autenticação JWT**: Sistema seguro de login e registro
- **CRUD Completo de Usuários**: Create, Read, Update e Delete
- **Validação de Dados**: Validação robusta de entradas
- **Segurança**: Hashing de senhas, proteção de rotas
- **Prisma ORM**: Acesso eficiente ao banco de dados
- **SQLite**: Banco de dados simples e eficiente

## 🛠️ Pré-requisitos

- Node.js (v16 ou superior)
- npm ou yarn
- NestJS CLI (opcional)

## 🚀 Instalação

1. **Clone o repositório**

```bash
git clone https://github.com/kewensilva-gif/authentication_nest
cd seu-projeto
```

2. **Instale as dependências**

```bash
npm install
# ou
yarn install
```

3. **Configure o ambiente**

Crie um arquivo `.env` na raiz do projeto baseado no `.env.example`:

```env
DATABASE_URL="file:./dev.db"
JWT_SECRET=seuSegredoSuperSecreto
JWT_EXPIRES_IN=80000s
```

4. **Execute as migrações do Prisma**

```bash
npx prisma migrate dev --name init
```

## 🏃 Executando o Projeto

**Modo de desenvolvimento:**

```bash
npm run start:dev
```

**Modo de produção:**

```bash
npm run build
npm run start:prod
```

## 📚 Estrutura do Projeto

```
src/
├── auth/               # Módulo de autenticação
│   ├── auth.service.ts # Lógica de autenticação
│   └── auth.controller.ts # Rotas de autenticação
├── users/              # Módulo de usuários
│   ├── users.service.ts # Lógica de usuários
│   └── users.controller.ts # Rotas de usuários
├── prisma/             # Configuração do Prisma
│   └── schema.prisma   # Schema do banco de dados
├── app.module.ts       # Módulo principal
└── main.ts             # Ponto de entrada
```

## 🔐 Rotas da API

### Autenticação
- `POST /auth/login` - Fazer login

### Usuários

- `POST /user` - Criar um novo usuário
- `GET /users` - Listar todos os usuários (requer autenticação)
- `GET /users/:id` - Obter um usuário específico (requer autenticação)
- `PATCH /users/:id` - Atualizar um usuário (requer autenticação)
- `DELETE /users/:id` - Remover um usuário (requer autenticação)

## 📝 Exemplos de Requisições

### Registrar um usuário

```bash
curl -X POST http://localhost:3000/user \
  -H "Content-Type: application/json" \
  -d '{
    "email": "usuario@exemplo.com",
    "password": "senhaSegura123",
    "name": "Nome do Usuário"
  }'
```

### Fazer login

```bash
curl -X POST http://localhost:3000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "usuario@exemplo.com",
    "password": "senhaSegura123"
  }'
```

### Acessar perfil (autenticado)

```bash
curl -X GET http://localhost:3000/auth/profile \
  -H "Authorization: Bearer <SEU_TOKEN_JWT>"
```

## 🧪 Testes

Para executar os testes:

```bash
npm run test
```

Para testes com cobertura:

```bash
npm run test:cov
```

## 🛡️ Segurança

- **Senhas**: Armazenadas com bcrypt
- **Tokens JWT**: Assinados com segredo configurável
- **Rotas protegidas**: Middleware de autenticação
- **Validação**: DTOs validados com class-validator

## 📦 Dependências Principais

- @nestjs/core: Framework NestJS
- @nestjs/jwt: Manipulação de JWT
- @nestjs/passport: Autenticação
- @prisma/client: ORM Prisma
- bcrypt: Hashing de senhas
- class-validator: Validação de dados
- passport-jwt: Estratégia JWT para Passport

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Distribuído sob a licença MIT. Veja `LICENSE` para mais informações.