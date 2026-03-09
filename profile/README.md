# 🎲 BraitoBet - Social Casino Platform

Bem-vindo ao repositório oficial da **BraitoBet**! 👋

Este é o nosso monorepo que contém todo o código-fonte da nossa plataforma de minigames focada em entretenimento (estilo Ludijogos). A economia da plataforma é baseada em **Braitocoins** (moeda estritamente virtual).

> ⚠️ **Aviso de Escopo:** Este projeto é um **Social Casino**. Não existe mecânica de retorno financeiro, cash out ou levantamento de dinheiro real.

---

## 🗺️ Mapa do Repositório (Monorepo)

O nosso projeto está dividido em três secções principais para facilitar a partilha de código e a escalabilidade:

### 💻 `apps/` — As Aplicações

- **`web/` (Frontend):** Construído com **SvelteKit**. Contém a interface do utilizador, a lógica visual dos minigames (Double, Truco), gestão de estado (Stores) e comunicação via WebSockets.
- **`api/` (Backend):** Construído com **Node.js + TypeScript**. É o coração lógico da plataforma, responsável por validar transações, gerir as salas multiplayer, o chat em tempo real e a comunicação segura com a base de dados.

### 📦 `packages/` — Código Partilhado

- **`shared/`:** Onde vive a nossa "fonte de verdade". Aqui guardamos todos os **Tipos (TypeScript)**, constantes globais e validações (Zod). Como é partilhado, garantimos que o Frontend e o Backend validam as regras exatamente da mesma forma.

### 🛠️ `infrastructure/` — Cloud & DevOps

- **`terraform/` & Docker:** Scripts de aprovisionamento para o **Google Cloud Platform** e containers.
- **Firestore Rules:** Ficheiros como `firestore.rules` que garantem a segurança da base de dados ao nível da infraestrutura.

---

## 🚀 Como Começar (Setup Local)

Para começares a contribuir para a BraitoBet, garante que tens o teu ambiente preparado.

### Pré-requisitos

| Ferramenta | Versão mínima |
|------------|---------------|
| Node.js    | `>= 20.0.0`   |
| pnpm       | `>= 9.0.0`    |
| Docker     | Instalado e ativo |

### Passo a Passo da Instalação

**1. Instalar as dependências do monorepo**

Na raiz do projeto, executa:

```bash
pnpm install
```

**2. Subir os serviços locais (Infraestrutura)**

Inicia os serviços de cache e rate limiting (Redis) em background:

```bash
docker-compose up -d
```

**3. Rodar em modo de desenvolvimento**

O comando abaixo utiliza o nosso gestor de tarefas para iniciar o SvelteKit e a API Node.js em simultâneo:

```bash
pnpm dev
```

---

## 🔒 Segurança e Regras de Negócio

Tratamos a nossa economia virtual com o mesmo rigor que um sistema financeiro real:

- **Atomicidade:** Qualquer funcionalidade que adicione ou remova Braitocoins deve obrigatoriamente usar **Firestore Transactions**.
- **Proteção contra Abuso:** Utilizamos **Idempotência** para evitar recargas duplicadas e o **Redis** como Rate Limiter nas rotas da API.
- **Provably Fair:** Os resultados dos minigames (como a Roleta/Double) devem ser verificáveis pelos jogadores.

---

## 🤝 Contribuições

- **Code Review:** Nunca faças commit diretamente para a branch `main`. Cria uma branch de funcionalidade (ex: `feature/chat-emojis`) e abre um **Pull Request**.
- **Documentação Extra:** Os guias visuais (Figma), o Documento de Produto e as atas de reuniões estão guardados no nosso **Google Drive Interno**. Consulta os líderes técnicos para obteres acesso se fores um novo membro da equipa.

---

*BraitoBet — Entretenimento Seguro e Divertido.* 🚀
