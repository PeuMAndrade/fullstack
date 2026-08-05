# Estudos independentes

Cada subdiretório representa uma camada da stack. Assim não existe ambiguidade — TypeScript no front e no back, Next.js cliente e servidor, cada um vai na camada correspondente.

## Camadas

| Camada       | O que cobre                                                    |
|-------------|----------------------------------------------------------------|
| frontend/   | React (componentes, hooks, estado), Bootstrap, CSS, TypeScript no cliente, Next.js Client Components |
| backend/    | Next.js Route Handlers, Server Actions, autenticação, TypeScript no servidor, validação |
| banco-de-dados/ | PostgreSQL, Prisma ORM (schema, migrations, queries), modelagem |

## Como estudar com Claude Code

1. Crie um arquivo `estudo/<camada>/sessao01.md` e escreva suas dúvidas
2. Peça ao Claude para explicar, gerar exemplos, revisar código, etc.
3. Salve os exemplos gerados em `estudo/<camada>/exemplos/`

### Exemplos de prompts

- **Frontend**: "Me explica como funcionam Server Components vs Client Components no Next.js"
- **Backend**: "Me mostra como criar uma API Route com validação Zod no Next.js"
- **Banco**: "Me explica como modelar um relacionamento N:N no Prisma"

