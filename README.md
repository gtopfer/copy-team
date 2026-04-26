# Copy Team

Time de 6 agentes de IA para criar copy de _build in public_ para Reddit e X, a partir de documentação técnica real.

O sistema ingere arquivos de contexto do produto, monitora redes sociais de referência e produz posts autênticos — sem fluff de marketing, com detalhes técnicos e voz de fundador.

---

## Como funciona

```
./input/ (docs do produto)
     │
     ▼
┌─────────┐
│  Leitor │  lê e estrutura o contexto
└────┬────┘
     │ contexto estruturado
     ├──────────────────────┐
     ▼                      ▼
┌─────────┐          ┌─────────────┐
│   CPO   │          │  Observador │  rodam em paralelo
└────┬────┘          └──────┬──────┘
     │ produto brief         │ inteligência social
     └──────────┬────────────┘
                ▼
        ┌──────────────┐
        │ Estrategista │  define quais momentos viram posts e como
        └──────┬───────┘
               │ plano de pauta
               ▼
          ┌─────────┐
          │ Redator │  escreve todos os copies (Reddit + X)
          └────┬────┘
               │ copies
               ▼
          ┌─────────┐
          │ Revisor │  checklist de qualidade; reescreve se necessário
          └────┬────┘
               │ copies aprovados
               ▼
       ./output/reddit/
       ./output/x/
```

---

## Pré-requisitos

- [Claude Code](https://claude.ai/code) (CLI)
- **Reddit MCP** — necessário para o Agente 3 (Observador)
- **X MCP** — necessário para o Agente 3 (Observador)

---

## Quick start

```bash
# 1. Clone o repositório
git clone <repo-url> && cd copy-team

# 2. Configure a persona da sua marca
#    Edite ./persona.md com voz, tom e exemplos reais

# 3. Configure as referências sociais
#    Edite ./references.md com contas de X e subreddits a monitorar

# 4. Coloque os arquivos de contexto do produto em ./input/
#    (TXT, MD, PDF, DOCX ou PPTX)

# 5. Rode
claude "Gere todos os copies com base nos arquivos em ./input/"
```

Os posts gerados aparecem em `./output/reddit/` e `./output/x/`.

---

## Agentes

| # | Agente | Modelo | Responsabilidade |
|---|--------|--------|-----------------|
| 1 | [Leitor](./agents/01-leitor.md) | Haiku | Lê os arquivos de input e extrai contexto estruturado |
| 2 | [CPO](./agents/02-cpo.md) | Sonnet | Traduz contexto técnico em linguagem de produto |
| 3 | [Observador](./agents/03-observador.md) | Haiku | Monitora redes sociais e extrai inteligência de tom/conteúdo |
| 4 | [Estrategista](./agents/04-estrategista.md) | Sonnet | Define quais momentos viram posts e como abordá-los |
| 5 | [Redator](./agents/05-redator.md) | Opus | Escreve todos os copies para Reddit e X |
| 6 | [Revisor](./agents/06-revisor.md) | Sonnet | Checklist de qualidade; reescreve o que não passa |

CPO e Observador rodam em paralelo — ambos recebem o output do Leitor e alimentam o Estrategista de forma independente.

---

## Configuração

### `persona.md`

Define a voz, tom e identidade da marca. O Redator e o Revisor leem este arquivo na íntegra antes de escrever ou revisar qualquer post. Inclui:

- Princípios de tom
- Voz por canal (Reddit, X, etc.)
- Pilares de conteúdo
- Público-alvo
- O que a marca **nunca** faz
- Exemplos de calibração (certo vs. errado)

### `references.md`

Lista as contas e subreddits que o Observador deve monitorar. Inclui:

- Contas de X a acompanhar (concorrentes, inspirações, conta própria)
- Subreddits relevantes para a comunidade
- Repositório GitHub do produto (fonte de verdade sobre o estado atual do build)

---

## Output

Cada post é salvo em um arquivo separado:

**Reddit** → `./output/reddit/NN-slug.md`

```markdown
# [Post title]

_Generated: [date]_
_Source: files in ./input/_
_Suggested subreddits: r/..., r/..., r/..._

---

[Full post body]
```

**X** → `./output/x/NN-slug.md`

```markdown
# [Post title or first line of thread]

_Generated: [date]_
_Source: files in ./input/_

---

[Full post or thread]
```

`NN` é o número sequencial com zero à esquerda (01, 02, ...).  
`slug` é o título em lowercase com hífens (ex: `01-antenna-placement-tradeoffs.md`).

---

## Estrutura do projeto

```
./
├── README.md
├── CLAUDE.md           ← instruções de orquestração para o Claude Code
├── persona.md          ← voz, tom e identidade da marca
├── references.md       ← contas e subreddits a monitorar
├── agents/
│   ├── 01-leitor.md
│   ├── 02-cpo.md
│   ├── 03-observador.md
│   ├── 04-estrategista.md
│   ├── 05-redator.md
│   └── 06-revisor.md
├── input/              ← coloque aqui os arquivos de contexto do produto
└── output/
    ├── reddit/         ← posts gerados para Reddit
    └── x/              ← posts gerados para X
```
