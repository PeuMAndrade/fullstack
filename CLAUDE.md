# Fullstack - 5º Semestre

Repositório da disciplina de Desenvolvimento Fullstack. Centraliza projetos, anotações de aula e sessões de estudo com Claude Code.

## Stack da disciplina

| Camada       | Tecnologia                          |
|-------------|-------------------------------------|
| Frontend     | React 19+, TypeScript, Bootstrap 5  |
| Framework    | Next.js (App Router)                |
| Backend      | Next.js API Routes / Route Handlers |
| Banco        | PostgreSQL (via Prisma ORM)         |
| Tooling      | Vite (projetos puros React), ESLint |

## Estrutura do repositório

```
anotacoes/     → notas de aula organizadas por data/tema
projetos/      → um diretório por projeto da disciplina
estudo/        → sessões de estudo por camada (frontend/, backend/, banco-de-dados/)
meu-projeto/   → scaffold inicial (Vite + React + TS)
```

## Convenções

- **Linguagem**: Todo conteúdo (anotações, READMEs, comentários) em português. Código em inglês.
- **Commits**: convencionais (`feat:`, `fix:`, `docs:`, `chore:`). Mensagens em português.
- **Formatação**: Prettier com defaults, ESLint config do Vite/Next.
- **Anotações**: Um arquivo `.md` por aula. Começar com metadados (data, tema, tópicos).

## Skills instaladas

### Educação (estudo e aprendizagem)
10 skills de pedagogia baseada em evidência em `.claude/skills/`:

| Skill | Use quando... |
|-------|---------------|
| `/retrieve-first-gate` | Forçar recall antes de receber explicação |
| `/stuck-and-error-diagnosis-coach` | Travar num bug — diagnosticar antes de corrigir |
| `/progressive-hint-ladder` | Precisar de dicas progressivas sem spoiler da resposta |
| `/ai-claim-checker` | Verificar criticamente o que a IA gerou |
| `/teach-back-evaluator` | Testar se realmente entendeu ensinando o conceito |
| `/explain-first-interrogator` | Explicar com suas palavras antes da IA avaliar |
| `/confidence-calibration-check` | Checar se sua confiança bate com seu conhecimento real |
| `/srl-session-wrapper` | Estruturar sessão de estudo com metacognição |
| `/transfer-bridge` | Verificar se consegue aplicar o conceito em contexto novo |
| `/productive-failure-protocol` | Enfrentar problema difícil antes de receber instrução |

### Engenharia (mattpocock/skills — 35 skills)
Skills essenciais de engenharia de software em `.claude/skills/`:

| Skill | Use quando... |
|-------|---------------|
| `/grill-me` | Antes de codar — Claude entrevista você sobre o plano (30-40 perguntas) |
| `/grill-with-docs` | Grill que gera CONTEXT.md e ADRs |
| `/tdd` | Red-green-refactor com fatias verticais |
| `/diagnosing-bugs` | Loop de debug em 6 fases: reproduz → hipótese → instrumenta → corrige |
| `/code-review` | Dois subagentes: padrões + aderência à spec |
| `/implement` | Orquestra build a partir de spec/tickets com TDD interno |
| `/to-spec` | Sintetiza conversa em spec formal |
| `/to-tickets` | Quebra spec em tickets independentes (fatias verticais) |
| `/teach` | Modo ensino cross-session |
| `/research` | Pesquisa fontes primárias e produz .md com citações |
| `/prototype` | Protótipo descartável pra testar ideias |
| `/handoff` | Comprime sessão pra outro agente continuar |

Demais skills: `ask-matt`, `codebase-design`, `domain-modeling`, `improve-codebase-architecture`, `triage`, `resolving-merge-conflicts`, `wayfinder`, `wizard`, `setup-pre-commit`, `git-guardrails-claude-code`, `loop-me`, `wait-what`, `writing-for-agents` e outras.

> Skills configuradas com `/setup-matt-pocock-skills`. Issues em `.scratch/`, labels canônicos, domain docs single-context.

### Stack (a instalar futuramente)
- `mindrally/skills` — `nextjs-react-typescript`, `prisma`, `postgresql-best-practices`, `scss-best-practices`

## Agent skills

### Issue tracker

Issues são arquivos markdown em `.scratch/<feature>/`. Skills como `to-tickets`, `triage` e `to-spec` leem e escrevem nesse diretório. Veja `docs/agents/issue-tracker.md`.

### Triage labels

Labels canônicos: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. Veja `docs/agents/triage-labels.md`.

### Domain docs

Single-context — um `CONTEXT.md` + `docs/adr/` na raiz do repo. Veja `docs/agents/domain.md`.

## Comportamento padrão

Estas regras definem quando as skills são ativadas automaticamente. Você não precisa digitar `/comando` — eu decido com base no contexto.

### 📖 Ao estudar um conceito novo (ex: "me explica X", "não entendi Y")

1. **`/retrieve-first-gate`** — Antes de qualquer explicação, pergunte o que já sei sobre o tópico. Peça recall livre + confiança 0-100. Trabalhe só nos gaps encontrados.
2. **`/explain-first-interrogator`** — Depois da explicação inicial, eu explico o conceito com minhas palavras. Sonde a parte mais fraca com perguntas (nunca correção direta). Máx. 3 rodadas.
3. **`/teach-back-evaluator`** — Ao final, eu ensino o conceito pra você (que finge ser um novato curioso). Pontue coerência, completude e risco de concepção errada (1-3).

### 🐛 Ao encontrar erros ou travar em código

4. **`/stuck-and-error-diagnosis-coach`** — Não dê a resposta. Classifique o erro primeiro: conceitual, procedural, estratégico ou representacional. Depois ajude direcionado ao tipo.
5. **`/progressive-hint-ladder`** — Se eu pedir dica, use a escada de 6 níveis. Nunca dê a solução completa. Exija reflexão antes de cada escalada.

### 🔍 Depois de gerar explicações, código ou respostas substantivas

6. **`/ai-claim-checker`** — Me ajude a verificar criticamente: (a) o que pode estar errado, (b) como eu verificaria, (c) qual fonte confiável consultar. Trate output de IA como claim a avaliar, não verdade absoluta.

### 🏗️ Antes de implementar qualquer feature ou mudança não-trivial

7. **`/grill-me`** — Me entreviste implacavelmente sobre o plano antes de escrever código. Caminhe cada ramo da árvore de decisão.

### 🧪 Ao escrever código novo ou corrigir bugs

8. **`/tdd`** — Red-green-refactor. Escreva teste que falha → faça passar → refatore. Use fatias verticais (uma feature end-to-end por vez).

### 📝 Ao final de uma sessão de estudo

9. **`/srl-session-wrapper`** — Wrap de metacognição: meta no início → check aos 15min → reflexão no final. O que eu sei agora que não sabia antes? O que mudar na próxima sessão?

### 🧠 Quando há suspeita de que não sei tanto quanto acho

10. **`/confidence-calibration-check`** — Confiança 0-100 antes e depois de testar conhecimento real. Identifique overconfidence (ilusão de competência) vs. underconfidence.

### 🌉 Quando demonstro que entendi algo

11. **`/transfer-bridge`** — Teste near-transfer (mesmo princípio, superfície diferente) e far-transfer (domínio diferente, mesma estrutura). Se não transfere, não foi aprendido.

### 💪 Ao enfrentar um conceito difícil pela primeira vez

12. **`/productive-failure-protocol`** — Deixe eu tentar resolver antes de receber instrução. Exija 2 tentativas genuínas. Só depois consolide referenciando minhas tentativas.

### 🔬 Ao revisar código pronto

13. **`/code-review`** — Dois subagentes em paralelo: um checa padrões de código, outro verifica se o código bate com a spec/tarefa.

## Para o Claude Code

- Este repositório é multidisciplinar — o mesmo workspace cobre projetos, estudo e anotações.
- Ao criar código, seguir os padrões do ecossistema React/Next/TypeScript.
- Ao revisar anotações, manter formatação consistente com os templates.
- Preferir explicações didáticas (sou estudante, estou aprendendo).
- **Importante**: As regras em `## Comportamento padrão` são obrigatórias, não sugestões. Siga-as proativamente — não espere eu pedir.
