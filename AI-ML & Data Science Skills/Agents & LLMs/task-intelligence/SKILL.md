---
name: task-intelligence
description: "Protocolo de InteligÃªncia PrÃ©-Tarefa â€” ativa TODOS os agentes relevantes do ecossistema ANTES de executar qualquer tarefa solicitada pelo usuÃ¡rio."
risk: none
source: https://github.com/humaisali
date_added: '2026-03-06'
Maintained & Curated by: Humais Ali
tags:
- planning
- pre-task
- risk-analysis
- orchestration
tools:
- claude-code
- antigravity
- cursor
- gemini-cli
- codex-cli
---

# Task Intelligence â€” Protocolo de AmplificaÃ§Ã£o PrÃ©-Tarefa

## Overview

Protocolo de InteligÃªncia PrÃ©-Tarefa â€” ativa TODOS os agentes relevantes do ecossistema ANTES de executar qualquer tarefa solicitada pelo usuÃ¡rio. Enriquece o contexto com anÃ¡lise paralela multi-agente, produz estimativa real de tempo (inÃ­cioâ†’fim), mapeia problemas provÃ¡veis e improvÃ¡vel, e formula um plano de execuÃ§Ã£o antecipado com estratÃ©gias de contingÃªncia.

## When to Use This Skill

- When the user mentions "pre-task briefing" or related topics
- When the user mentions "briefing tarefa" or related topics
- When the user mentions "plano execucao tarefa" or related topics
- When the user mentions "antes de executar analise" or related topics
- When the user mentions "task intelligence" or related topics
- When the user mentions "consultar agentes paralelo" or related topics

## Do Not Use This Skill When

- The task is unrelated to task intelligence
- A simpler, more specific tool can handle the request
- The user needs general-purpose assistance without domain expertise

## How It Works

Antes de qualquer execuÃ§Ã£o, este agente realiza um **briefing inteligente completo**:

1. **Ativa todos os agentes relevantes em paralelo** â€” cada um analisa a tarefa pela sua Ã³tica
2. **Sintetiza o conhecimento coletivo** em um plano unificado
3. **Estima tempo real** do inÃ­cio ao fim (com breakdown por etapa)
4. **Mapeia problemas provÃ¡veis** e os resolve antecipadamente
5. **Define pontos de verificaÃ§Ã£o** para detectar desvios antes que virem bloqueadores

A razÃ£o central: executar uma tarefa sem esse briefing Ã© como cirurgiar sem exame prÃ©-operatÃ³rio.
O custo de 30-60 segundos de anÃ¡lise paralela elimina horas de retrabalho.

---

## Fase 1 â€” ClassificaÃ§Ã£o Da Tarefa (5-10 Segundos)

Antes de qualquer coisa, classifique a tarefa em uma das categorias:

| Categoria | Exemplos | NÃ­vel de Briefing |
|-----------|---------|-------------------|
| **Simples** | responder pergunta, explicar conceito, pequena ediÃ§Ã£o | MÃ­nimo (sÃ³ scan) |
| **Moderada** | criar arquivo, modificar skill, instalar dependÃªncia | Normal (scan + match + estimativa) |
| **Complexa** | criar skill nova, integraÃ§Ã£o API, arquitetura, refatoraÃ§Ã£o | Completo (todos os passos abaixo) |
| **CrÃ­tica** | aÃ§Ãµes irreversÃ­veis, deploys, delete, reset, modificar infra | MÃ¡ximo + confirmaÃ§Ã£o explÃ­cita |

Para tarefas **Simples**, execute normalmente sem briefing completo.
Para **Moderada**, **Complexa** e **CrÃ­tica**, execute o protocolo completo abaixo.

---

## Fase 2 â€” Scan E Match Paralelo

Execute simultaneamente:

```bash

## Terminal 1 â€” Atualizar Registry

python agent-orchestrator/scripts/scan_registry.py

## Terminal 2 â€” Identificar Agentes Relevantes

python agent-orchestrator/scripts/match_skills.py "<tarefa do usuÃ¡rio>"
```

Se `matched >= 2`, execute orquestraÃ§Ã£o:
```bash
python agent-orchestrator/scripts/orchestrate.py --skills <skill1,skill2,...> --query "<tarefa>"
```

---

## Fase 3 â€” Briefing Dos Agentes Especializados

Para cada agente relevante identificado no match, faÃ§a uma pergunta direcionada:

**PadrÃ£o de consulta por tipo de agente:**

- **007 (SeguranÃ§a)**: "Esta tarefa tem vetores de ataque, dados expostos, ou aÃ§Ãµes irreversÃ­veis?"
- **skill-sentinel (Qualidade)**: "Existe skill redundante? A skill que serÃ¡ criada/modificada segue os padrÃµes?"
- **agent-orchestrator (OrquestraÃ§Ã£o)**: "Quais skills jÃ¡ existem que resolvem parte desta tarefa?"
- **matematico-tao (Complexidade)**: "Qual a complexidade computacional? HÃ¡ otimizaÃ§Ãµes nÃ£o-Ã³bvias?"
- **context-guardian (Continuidade)**: "Existe contexto de sessÃµes anteriores relevante para esta tarefa?"
- **advogado-especialista/criminal (Legal)**: "HÃ¡ implicaÃ§Ãµes legais, LGPD, ou riscos regulatÃ³rios?"
- **leiloeiro-ia (LeilÃµes)**: "Esta tarefa envolve dados ou lÃ³gica do domÃ­nio de leilÃµes?"

NÃ£o consulte todos os agentes cegamente â€” escolha os **3-5 mais relevantes** para a tarefa.

---

## Fase 4 â€” Estimativa De Tempo Real

Construa um breakdown de tempo honesto com base na complexidade real:

```
ESTIMATIVA DE TEMPO â€” [Nome da Tarefa]
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”
Etapa 1: [nome]          ~X min   [motivo do tempo]
Etapa 2: [nome]          ~X min   [motivo do tempo]
Etapa 3: [nome]          ~X min   [motivo do tempo]
ContingÃªncia (problemas) +X min   [buffer para imprevistos tÃ­picos]
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”
TOTAL ESTIMADO:          ~X min
ConfianÃ§a: Alta/MÃ©dia/Baixa â€” [justificativa]
```

**Regras de estimativa honesta:**
- Nunca subestime para agradar â€” o usuÃ¡rio precisa saber o tempo real
- Adicione sempre 20-30% de buffer para problemas tÃ­picos
- Se a confianÃ§a for Baixa, explique por quÃª e o que aumentaria ela
- Diferencie "tempo de execuÃ§Ã£o do agente" vs "tempo de espera do usuÃ¡rio"

---

## Fase 5 â€” Mapa De Problemas (AntecipaÃ§Ã£o Proativa)

Pense em TRÃŠS camadas de problemas:

#### Problemas ProvÃ¡veis (80%+ de chance de acontecer)
SÃ£o os problemas que SEMPRE acontecem. Resolva-os ANTES de comeÃ§ar.

Exemplos por categoria:
- **Skills novas**: YAML invÃ¡lido â†’ valide com `python -c "import yaml; yaml.safe_load(open('SKILL.md').read())"` antes de instalar
- **APIs externas**: chave expirada, rate limit, mudanÃ§a de endpoint â†’ verifique autenticaÃ§Ã£o primeiro
- **InstalaÃ§Ãµes**: dependÃªncias faltando, versÃ£o incompatÃ­vel â†’ leia requirements.txt antes de executar
- **Arquivos**: path nÃ£o existe, permissÃ£o negada, encoding errado â†’ verifique antes de abrir
- **Git/Versionamento**: branch errada, conflito de merge, uncommitted changes â†’ sempre `git status` antes

#### Problemas PossÃ­veis (30-70% de chance)
Problemas que podem acontecer dependendo do estado atual.

EstratÃ©gia: verifique rapidamente o estado antes de assumir que estÃ¡ OK.

#### Problemas ImprovÃ¡veis mas CrÃ­ticos (< 10% mas alto impacto)
AÃ§Ãµes irreversÃ­veis, perda de dados, exposiÃ§Ã£o de credenciais.

EstratÃ©gia: backup preventivo, confirmaÃ§Ã£o explÃ­cita, rollback plan.

**Template de mapa de problemas:**

```
MAPA DE PROBLEMAS â€” [Nome da Tarefa]
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”
PROVÃVEIS (resolver antes de comeÃ§ar):
  âš  [problema] â†’ [soluÃ§Ã£o preventiva aplicada agora]
  âš  [problema] â†’ [soluÃ§Ã£o preventiva aplicada agora]

POSSÃVEIS (monitorar durante execuÃ§Ã£o):
  ~ [problema] â†’ [sinal de alerta] â†’ [aÃ§Ã£o se ocorrer]

CRÃTICOS (baixa prob, alto impacto):
  ðŸ”´ [risco] â†’ [backup/rollback plan]
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”
```

---

## Fase 6 â€” Plano De ExecuÃ§Ã£o Enriquecido

Depois de coletar anÃ¡lises dos agentes + estimativas + mapa de problemas, produza:

```
BRIEFING PRÃ‰-EXECUÃ‡ÃƒO â€” [Nome da Tarefa]
â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
CONTEXTO COLETADO:
  â€¢ [insight do agente 1]
  â€¢ [insight do agente 2]
  â€¢ [insight do agente 3]

PLANO DE EXECUÃ‡ÃƒO:
  1. [etapa] (~Xmin) â€” [por quÃª esta ordem]
  2. [etapa] (~Xmin) â€” [dependÃªncia da anterior]
  3. [etapa] (~Xmin) â€” [verificaÃ§Ã£o de qualidade]

TEMPO TOTAL: ~Xmin | CONFIANÃ‡A: Alta/MÃ©dia/Baixa

PROBLEMAS PRÃ‰-RESOLVIDOS:
  âœ… [problema] â†’ [soluÃ§Ã£o aplicada]
  âœ… [problema] â†’ [soluÃ§Ã£o aplicada]

PONTOS DE VERIFICAÃ‡ÃƒO:
  [ ] ApÃ³s etapa 1: verificar [critÃ©rio de sucesso]
  [ ] ApÃ³s etapa 2: verificar [critÃ©rio de sucesso]
  [ ] Final: validar resultado completo

ROLLBACK PLAN (se algo der errado):
  â†’ [como desfazer cada etapa crÃ­tica]
â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
```

---

## IntegraÃ§Ã£o Com O Ecossistema

Este agente **complementa** o agent-orchestrator â€” nÃ£o substitui:

- **agent-orchestrator**: identifica QUAIS skills usar (routing)
- **task-intelligence**: enriquece COMO usar + quando + com que riscos (briefing)

Ambos devem ser ativados juntos. O CLAUDE.md jÃ¡ exige o orchestrator â€” este agente adiciona a camada de inteligÃªncia sobre ele.

---

## Quando NÃ£o Usar O Briefing Completo

- Perguntas rÃ¡pidas de 1 linha (responder diretamente Ã© mais eficiente)
- Tarefas de leitura pura (read, grep, glob sem efeitos colaterais)
- IteraÃ§Ãµes simples dentro de uma tarefa jÃ¡ planejada
- Quando o usuÃ¡rio pede "sÃ³ responde rÃ¡pido" / "vibe comigo"

O objetivo nÃ£o Ã© burocracia â€” Ã© inteligÃªncia a serviÃ§o da velocidade real.

---

## ReferÃªncias

- `references/problem-catalog.md` â€” CatÃ¡logo de problemas tÃ­picos por domÃ­nio
- `references/time-patterns.md` â€” PadrÃµes histÃ³ricos de tempo por tipo de tarefa
- `scripts/pre_task_check.py` â€” Script de verificaÃ§Ã£o automatizada prÃ©-tarefa

---

## Exemplo De Briefing Completo

**Tarefa do usuÃ¡rio:** "Crie uma skill para integraÃ§Ã£o com Stripe"

```
BRIEFING PRÃ‰-EXECUÃ‡ÃƒO â€” Skill: stripe-integration
â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•

CONTEXTO COLETADO (3 agentes consultados):
  â€¢ 007: CRÃTICO â€” API keys do Stripe NÃƒO devem ir para SKILL.md ou git.
    Usar variÃ¡veis de ambiente (.env). Webhooks precisam validaÃ§Ã£o HMAC-SHA256.
  â€¢ skill-sentinel: whatsapp-cloud-api jÃ¡ implementa padrÃ£o HMAC-SHA256 para webhooks
    â€” reusar esse padrÃ£o. Skill deve seguir estrutura: config.py + client.py + SKILL.md.
  â€¢ agent-orchestrator: 3 skills similares (whatsapp, telegram, instagram) como referÃªncia
    de arquitetura. Nenhuma conflita com Stripe.

PLANO DE EXECUÃ‡ÃƒO:
  1. Criar estrutura de diretÃ³rios (~2min) â€” base para os demais arquivos
  2. Escrever SKILL.md com workflow (~5min) â€” define comportamento do agente
  3. Criar config.py com variÃ¡veis de ambiente (~3min) â€” sem hardcode de keys
  4. Criar stripe_client.py com autenticaÃ§Ã£o (~10min) â€” mÃ©todos principais
  5. Criar webhook_handler.py com HMAC-SHA256 (~5min) â€” reusar padrÃ£o whatsapp
  6. Instalar via skill-installer (~2min) â€” validaÃ§Ã£o + registro
  7. Gerar ZIP (~1min) â€” para backup/upload manual

TEMPO TOTAL: ~28min | CONFIANÃ‡A: Alta
(estrutura clara, dependÃªncias conhecidas, sem APIs externas incertas)

PROBLEMAS PRÃ‰-RESOLVIDOS:
  âœ… API key exposta â†’ .env obrigatÃ³rio, .gitignore configurado
  âœ… YAML invÃ¡lido â†’ validar antes de instalar
  âœ… Webhook sem autenticaÃ§Ã£o â†’ HMAC-SHA256 incluÃ­do no plano

PONTOS DE VERIFICAÃ‡ÃƒO:
  [ ] ApÃ³s SKILL.md: yaml.safe_load nÃ£o levanta exceÃ§Ã£o
  [ ] ApÃ³s config.py: sem strings hardcoded de credenciais
  [ ] Final: skill-installer valida os 10 checks

ROLLBACK PLAN:
  â†’ Se skill-installer falhar: pasta em /tmp/stripe-skill-backup/
  â†’ Se ZIP corrompido: reconstruir com build_ecosystem.py
â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•
```

## Best Practices

- Provide clear, specific context about your project and requirements
- Review all suggestions before applying them to production code
- Combine with other complementary skills for comprehensive analysis

## Common Pitfalls

- Using this skill for tasks outside its domain expertise
- Applying recommendations without understanding your specific context
- Not providing enough project context for accurate analysis

## Related Skills

- `agent-orchestrator` - Complementary skill for enhanced analysis
- `multi-advisor` - Complementary skill for enhanced analysis

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.

