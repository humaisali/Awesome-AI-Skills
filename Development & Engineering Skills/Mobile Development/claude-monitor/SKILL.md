---
name: claude-monitor
description: Monitor de performance do Claude Code e sistema local. Diagnostica lentidao, mede CPU/RAM/disco, verifica API latency e gera relatorios de saude do sistema.
risk: safe
source: https://github.com/humaisali
date_added: '2026-03-06'
Maintained & Curated by: Humais Ali
tags:
- monitoring
- performance
- diagnostics
- system-health
tools:
- claude-code
- antigravity
- cursor
- gemini-cli
- codex-cli
---

# Claude Monitor â€” DiagnÃ³stico de Performance

## Overview

Monitor de performance do Claude Code e sistema local. Diagnostica lentidao, mede CPU/RAM/disco, verifica API latency e gera relatorios de saude do sistema.

## When to Use This Skill

- When the user mentions "lento" or related topics
- When the user mentions "lentidao" or related topics
- When the user mentions "lag" or related topics
- When the user mentions "lagado" or related topics
- When the user mentions "travando" or related topics
- When the user mentions "claude lento" or related topics

## Do Not Use This Skill When

- The task is unrelated to claude monitor
- A simpler, more specific tool can handle the request
- The user needs general-purpose assistance without domain expertise

## How It Works

Skill para diagnosticar e resolver problemas de lentidÃ£o no Claude Code e no sistema.
Determina se o gargalo Ã© local (PC) ou remoto (API Claude) e sugere aÃ§Ãµes corretivas.

## Quando Usar

- UsuÃ¡rio reclama que o Claude Code estÃ¡ lento ou travando
- Troca de sessÃµes de conversa demora para carregar
- Respostas do Claude demoram muito
- PC parece lento enquanto usa o Claude Code
- Qualquer menÃ§Ã£o a performance, lag, lentidÃ£o

## 1. DiagnÃ³stico RÃ¡pido (Health_Check.Py)

Rode SEMPRE como primeiro passo:

```bash
python C:\Users\renat\skills\claude-monitor\scripts\health_check.py
```

O script analisa em ~3 segundos:
- **CPU**: Uso atual e por core. >80% = gargalo provÃ¡vel
- **RAM**: Total, usada, disponÃ­vel. >85% = pressÃ£o de memÃ³ria
- **Browsers**: Processos e RAM por browser. >5GB total = excesso de abas
- **Claude Code**: Processos e RAM consumida
- **Disco**: EspaÃ§o livre. <10% = impacto em swap/performance
- **Rede**: LatÃªncia ao endpoint da API Claude
- **DiagnÃ³stico**: ClassificaÃ§Ã£o automÃ¡tica do problema com sugestÃµes

## 2. Interpretar O Resultado

O script retorna um JSON com `diagnosis` contendo:

- `bottleneck`: "cpu" | "ram" | "browsers" | "disk" | "network" | "claude_api" | "ok"
- `severity`: "critical" | "warning" | "ok"
- `suggestions`: Lista de aÃ§Ãµes recomendadas
- `summary`: Resumo em portuguÃªs para mostrar ao usuÃ¡rio

**Mostre o `summary` ao usuÃ¡rio** e ofereÃ§a executar as sugestÃµes.

## 3. AÃ§Ãµes Corretivas AutomÃ¡ticas

Baseado no diagnÃ³stico, ofereÃ§a ao usuÃ¡rio:

#### Se CPU alta (>80%):
- Listar processos consumindo mais CPU
- Sugerir fechar processos pesados desnecessÃ¡rios
- Verificar se Windows Update estÃ¡ rodando em background

#### Se browsers pesados (>5GB RAM ou >40 processos):
```bash
python C:\Users\renat\skills\claude-monitor\scripts\health_check.py --browsers-detail
```
Mostra RAM por browser e sugere quais fechar. **Nunca fechar processos sem permissÃ£o explÃ­cita do usuÃ¡rio.**

#### Se disco cheio (>85%):
- Mostrar pastas maiores
- Sugerir limpeza de Temp, cache de browsers, lixeira

#### Se rede lenta (latÃªncia >500ms):
- Testar conexÃ£o com api.anthropic.com
- Sugerir verificar VPN, proxy, ou conexÃ£o WiFi

## 4. Monitor ContÃ­nuo (Opcional)

Se o usuÃ¡rio quiser monitoramento em background:

```bash
python C:\Users\renat\skills\claude-monitor\scripts\monitor.py --interval 30 --duration 300
```

ParÃ¢metros:
- `--interval`: Segundos entre cada amostra (default: 30)
- `--duration`: DuraÃ§Ã£o total em segundos (default: 300 = 5 min)
- `--output`: Caminho do arquivo de log (default: monitor_log.json)
- `--alert-cpu`: Threshold de CPU para alerta (default: 80)
- `--alert-ram`: Threshold de RAM % para alerta (default: 85)

O monitor salva snapshots periÃ³dicos e gera um relatÃ³rio ao final com:
- Picos de CPU e RAM
- TendÃªncia (melhorando/piorando/estÃ¡vel)
- Eventos de alerta detectados
- RecomendaÃ§Ã£o final

## 5. Benchmark Da Api Claude (Opcional)

Para testar se a lentidÃ£o Ã© da API:

```bash
python C:\Users\renat\skills\claude-monitor\scripts\api_bench.py
```

Mede o tempo de resposta do processo Claude Code local (nÃ£o faz chamadas Ã  API).
Compara com tempos tÃ­picos e indica se estÃ¡ dentro do esperado.

## Thresholds De ReferÃªncia

| MÃ©trica | OK | Warning | Critical |
|---------|-----|---------|----------|
| CPU % | <60% | 60-85% | >85% |
| RAM usada % | <70% | 70-85% | >85% |
| RAM browsers | <3 GB | 3-6 GB | >6 GB |
| Processos browser | <30 | 30-60 | >60 |
| Disco livre | >15% | 10-15% | <10% |
| LatÃªncia rede | <200ms | 200-500ms | >500ms |

## Dicas Para O UsuÃ¡rio

Quando apresentar o diagnÃ³stico, inclua estas dicas contextuais:

- **Muitas abas = muito CPU/RAM**: Cada aba de browser Ã© um processo separado.
  50 abas = 50 processos competindo por recursos.
- **Claude Code Ã© pesado**: Ele roda vÃ¡rios processos Electron. Ã‰ normal consumir 3-5 GB.
  Mas se estiver usando >6 GB com vÃ¡rias sessÃµes, considere fechar sessÃµes antigas.
- **Troca de sessÃ£o lenta**: Geralmente causada por CPU alta ou muitos processos competindo.
  A sessÃ£o precisa carregar o histÃ³rico da conversa, e se o CPU estÃ¡ ocupado, demora.
- **Disco quase cheio**: Afeta a velocidade do swap (memÃ³ria virtual) e pode causar
  lentidÃ£o generalizada.

## DependÃªncias

- Python 3.10+
- psutil (instalado automaticamente pelo script se nÃ£o disponÃ­vel)
- Nenhuma API key necessÃ¡ria

## Best Practices

- Provide clear, specific context about your project and requirements
- Review all suggestions before applying them to production code
- Combine with other complementary skills for comprehensive analysis

## Common Pitfalls

- Using this skill for tasks outside its domain expertise
- Applying recommendations without understanding your specific context
- Not providing enough project context for accurate analysis

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.

