# 🚀 Laravel + Vue — Sistema com Autenticação e Dashboard

Aplicação full-stack com **Laravel** no backend e **Vue.js** no frontend, contendo sistema completo de **login**, **registro de usuários** e **dashboard** com listagem de usuários cadastrados.

---

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter instalado na sua máquina:

- [PHP](https://www.php.net/) >= 8.1
- [Composer](https://getcomposer.org/)
- [Node.js](https://nodejs.org/) >= 18.x e npm
- [Git](https://git-scm.com/)
- Banco de dados: **MySQL**, **PostgreSQL** ou **SQLite**

---

## ⚙️ Instalação e configuração

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

### 2. Instale as dependências do PHP

```bash
composer install
```

### 3. Instale as dependências do Node.js

```bash
npm install
```

### 4. Configure o arquivo de ambiente

Copie o arquivo de exemplo e renomeie:

```bash
cp .env.example .env
```

Abra o arquivo `.env` e confirme que a configuração do banco está assim:

```env
DB_CONNECTION=sqlite
```

Em seguida, crie o arquivo do banco de dados:

```bash
touch database/database.sqlite
```

> 💡 **Dica:** No Windows, use `New-Item database/database.sqlite` no PowerShell, ou crie o arquivo manualmente pela IDE.

### 5. Gere a chave da aplicação

```bash
php artisan key:generate
```

### 6. Execute as migrations

```bash
php artisan migrate
```

---

## ▶️ Rodando o projeto

Você precisa de **dois terminais abertos** simultaneamente — um para o Laravel e outro para o Vue.

### Terminal 1 — Servidor Laravel

```bash
php artisan serve
```

O backend estará disponível em: `http://localhost:8000`

### Terminal 2 — Frontend Vue (Vite)

```bash
npm run dev
```

O frontend estará disponível em: `http://localhost:5173` (ou conforme indicado no terminal)

---

## 🌐 Acessando a aplicação

| Rota | Descrição |
|------|-----------|
| `/register` | Cadastro de novo usuário |
| `/login` | Login na aplicação |
| `/dashboard` | Dashboard com listagem de usuários (requer login) |

---

## 📁 Estrutura do projeto

```
├── app/
│   ├── Http/Controllers/    # Controllers da aplicação
│   └── Models/              # Models Eloquent
├── database/
│   └── migrations/          # Migrations do banco de dados
├── resources/
│   ├── js/                  # Componentes Vue.js
│   └── views/               # Views Blade (entrada do Vue)
├── routes/
│   ├── web.php              # Rotas web
│   └── api.php              # Rotas da API
└── .env.example             # Exemplo de configuração de ambiente
```

---

## 🛠️ Comandos úteis

| Comando | Descrição |
|---------|-----------|
| `php artisan migrate:fresh` | Recria todas as tabelas do zero |
| `php artisan migrate:fresh --seed` | Recria as tabelas e popula com dados de teste |
| `php artisan route:list` | Lista todas as rotas disponíveis |
| `npm run build` | Gera os assets para produção |

---

## ❓ Possíveis problemas

**Erro de permissão nas pastas `storage` e `bootstrap/cache`:**
```bash
chmod -R 775 storage bootstrap/cache
```

**Erro de chave de aplicação:**
```bash
php artisan key:generate
```

**Dependências desatualizadas:**
```bash
composer update
npm update
```

---

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.