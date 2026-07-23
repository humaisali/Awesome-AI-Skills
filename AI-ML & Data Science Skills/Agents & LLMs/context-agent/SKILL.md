---
name: context-agent
description: Agente de contexto para continuidade entre sessoes. Salva resumos, decisoes, tarefas pendentes e carrega briefing automatico na sessao seguinte.
risk: safe
source: https://github.com/humaisali
date_added: '2026-03-06'
Maintained & Curated by: Humais Ali
tags:
- context
- session-management
- continuity
- memory
tools:
- claude-code
- antigravity
- cursor
- gemini-cli
- codex-cli
---

# Context Agent

## Overview

Agente de contexto para continuidade entre sessoes. Salva resumos, decisoes, tarefas pendentes e carrega briefing automatico na sessao seguinte.

## When to Use This Skill

- When the user mentions "salvar contexto" or related topics
- When the user mentions "salva o contexto" or related topics
- When the user mentions "proxima sessao" or related topics
- When the user mentions "briefing sessao" or related topics
- When the user mentions "resumo sessao" or related topics
- When the user mentions "continuidade sessao" or related topics

## Do Not Use This Skill When

- The task is unrelated to context agent
- A simpler, more specific tool can handle the request
- The user needs general-purpose assistance without domain expertise

## How It Works

Continuidade perfeita entre sessÃµes do Claude Code. Captura, comprime e
restaura contexto automaticamente â€” tÃ³picos, decisÃµes, tarefas, erros,
arquivos modificados e descobertas tÃ©cnicas.

## LocalizaÃ§Ã£o

```
C:\Users\renat\skills\context-agent\
â”œâ”€â”€ SKILL.md
â”œâ”€â”€ scripts/
â”‚   â”œâ”€â”€ config.py               # Paths e constantes
â”‚   â”œâ”€â”€ models.py               # Dataclasses
â”‚   â”œâ”€â”€ session_parser.py       # Parser JSONL do Claude Code
â”‚   â”œâ”€â”€ session_summary.py      # Gerador de resumos
â”‚   â”œâ”€â”€ active_context.py       # Gerencia ACTIVE_CONTEXT.md
â”‚   â”œâ”€â”€ project_registry.py     # Registro de projetos
â”‚   â”œâ”€â”€ compressor.py           # CompressÃ£o e arquivamento
â”‚   â”œâ”€â”€ search.py               # Busca FTS5
â”‚   â”œâ”€â”€ context_loader.py       # Carrega contexto
â”‚   â””â”€â”€ context_manager.py      # CLI entry point
â”œâ”€â”€ references/
â”‚   â”œâ”€â”€ context-format.md       # EspecificaÃ§Ã£o de formatos
â”‚   â””â”€â”€ compression-rules.md    # Regras de compressÃ£o
â””â”€â”€ data/
    â”œâ”€â”€ sessions/               # session-001.md, session-002.md, ...
    â”œâ”€â”€ archive/                # SessÃµes arquivadas
    â”œâ”€â”€ ACTIVE_CONTEXT.md       # Contexto consolidado (max 150 linhas)
    â”œâ”€â”€ PROJECT_REGISTRY.md     # Status de todos os projetos
    â””â”€â”€ context.db              # SQLite FTS5 para busca
```

## InicializaÃ§Ã£o (Primeira Vez)

```bash
python C:\Users\renat\skills\context-agent\scripts\context_manager.py init
```

## Salvar Contexto Da SessÃ£o Atual

Quando a sessÃ£o estÃ¡ terminando ou antes de uma tarefa longa, salvar o contexto:

```bash
python C:\Users\renat\skills\context-agent\scripts\context_manager.py save
```

O que faz:
1. Encontra o arquivo JSONL mais recente da sessÃ£o
2. Analisa todas as mensagens, tool calls e resultados
3. Gera resumo estruturado (session-NNN.md)
4. Atualiza ACTIVE_CONTEXT.md com novas informaÃ§Ãµes
5. Sincroniza com MEMORY.md (carregado no system prompt)
6. Indexa para busca full-text

## Carregar Contexto (Briefing)

No inÃ­cio de uma nova sessÃ£o, carregar o contexto:

```bash
python C:\Users\renat\skills\context-agent\scripts\context_manager.py load
```

Gera briefing com: projetos ativos, tarefas pendentes (por prioridade),
bloqueadores, decisÃµes recentes, convenÃ§Ãµes e resumo das Ãºltimas sessÃµes.

## Status RÃ¡pido

```bash
python C:\Users\renat\skills\context-agent\scripts\context_manager.py status
```

Resumo em poucas linhas: projetos, pendÃªncias crÃ­ticas, bloqueadores.

## Buscar No HistÃ³rico

```bash
python C:\Users\renat\skills\context-agent\scripts\context_manager.py search "rate limit"
```

Busca full-text (SQLite FTS5) em todas as sessÃµes â€” tÃ³picos, decisÃµes,
erros, arquivos, etc.

## ManutenÃ§Ã£o

```bash
python C:\Users\renat\skills\context-agent\scripts\context_manager.py maintain
```

Arquiva sessÃµes antigas, comprime arquivo, ressincroniza MEMORY.md,
reconstrÃ³i Ã­ndice de busca.

## Fluxo De Trabalho

```
[SessÃ£o termina]
  â†’ save â†’ session-NNN.md + ACTIVE_CONTEXT.md + MEMORY.md

[Nova sessÃ£o comeÃ§a]
  â†’ MEMORY.md jÃ¡ estÃ¡ no system prompt (automÃ¡tico)
  â†’ load â†’ briefing detalhado com tudo que precisa saber

[Contexto cresce demais]
  â†’ maintain â†’ arquiva sessÃµes antigas, comprime, otimiza
```

## O Que Ã‰ Capturado Em Cada SessÃ£o

- **TÃ³picos**: assuntos discutidos
- **DecisÃµes**: escolhas tÃ©cnicas e de arquitetura
- **Tarefas concluÃ­das**: o que foi feito
- **Tarefas pendentes**: o que falta (com prioridade)
- **Arquivos modificados**: quais arquivos foram editados/criados
- **Descobertas**: insights tÃ©cnicos importantes
- **Erros resolvidos**: problemas e suas soluÃ§Ãµes
- **QuestÃµes em aberto**: perguntas sem resposta
- **MÃ©tricas**: tokens consumidos, mensagens, tool calls

## IntegraÃ§Ã£o Com Memory.Md

O ACTIVE_CONTEXT.md Ã© automaticamente copiado para:
`C:\Users\renat\.claude\projects\C--Users-renat-skills\memory\MEMORY.md`

Como o MEMORY.md Ã© incluÃ­do no system prompt de toda sessÃ£o, o Claude
sempre comeÃ§a sabendo o estado atual dos projetos, tarefas pendentes
e decisÃµes tomadas â€” sem precisar de nenhuma aÃ§Ã£o manual.

## ReferÃªncias

- Para formato detalhado dos arquivos: `references/context-format.md`
- Para regras de compressÃ£o e arquivamento: `references/compression-rules.md`

## Best Practices

- Provide clear, specific context about your project and requirements
- Review all suggestions before applying them to production code
- Combine with other complementary skills for comprehensive analysis

## Common Pitfalls

- Using this skill for tasks outside its domain expertise
- Applying recommendations without understanding your specific context
- Not providing enough project context for accurate analysis

## Related Skills

- `context-guardian` - Complementary skill for enhanced analysis

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.

