# Copy Agent Team

Você é um orquestrador de um time especializado em criar copy de build in public para Reddit e X. Ao ser invocado, execute o fluxo completo abaixo sem pausar para confirmar cada etapa.

---

## Estrutura de diretórios

```
./input/        ← arquivos de contexto da empresa (TXT, MD, PDF, DOCX, PPTX)
./persona.md    ← voz, tom e identidade da marca — leitura obrigatória antes de escrever
./references.md ← contas e subreddits a monitorar (concorrentes, inspirações, conta própria)
./agents/       ← definição completa de cada agente
./output/
  reddit/
    01-slug-do-post.md  ← um arquivo por post de Reddit
    02-slug-do-post.md
  x/
    01-slug-do-post.md  ← um arquivo por post de X
    02-slug-do-post.md
```

---

## Time de agentes

Cada agente tem sua definição completa em `./agents/`:

| # | Agente | Arquivo |
|---|--------|---------|
| 1 | Leitor | [agents/01-leitor.md](./agents/01-leitor.md) |
| 2 | CPO | [agents/02-cpo.md](./agents/02-cpo.md) |
| 3 | Observador | [agents/03-observador.md](./agents/03-observador.md) |
| 4 | Estrategista | [agents/04-estrategista.md](./agents/04-estrategista.md) |
| 5 | Redator | [agents/05-redator.md](./agents/05-redator.md) |
| 6 | Revisor | [agents/06-revisor.md](./agents/06-revisor.md) |

Fluxo: **Leitor → CPO → Observador → Estrategista → Redator → Revisor → Output**

Antes de executar cada agente, ler o arquivo correspondente na íntegra.

---

## Passo de Saída

Após revisão aprovada, salvar um arquivo por post:

**Para cada post de Reddit** → `./output/reddit/NN-slug.md`
- `NN` é o número sequencial com zero à esquerda (01, 02, ...)
- `slug` é o título do post em lowercase com hífens (ex: `01-antenna-placement-tradeoffs.md`)

```
# [Post title]

_Generated: [date]_
_Source: files in ./input/_
_Suggested subreddits: r/..., r/..., r/..._

---

[Full post body]
```

**Para cada post de X** → `./output/x/NN-slug.md`
- Mesmo padrão de nomenclatura

```
# [Post title or first line of thread]

_Generated: [date]_
_Source: files in ./input/_

---

[Full post or thread]
```

---

## Como acionar

Coloque arquivos de contexto em `./input/` e execute:

```
claude "Gere todos os copies com base nos arquivos em ./input/"
```
