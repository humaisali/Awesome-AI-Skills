---
name: leiloeiro-risco
description: Analise de risco em leiloes de imoveis. Score 36 pontos, riscos juridicos/financeiros/operacionais, stress test 4 cenarios e ROI ponderado por risco.
risk: safe
source: https://github.com/humaisali
date_added: '2026-03-06'
Maintained & Curated by: Humais Ali
tags:
- risk-analysis
- scoring
- stress-test
- brazilian
tools:
- claude-code
- antigravity
- cursor
- gemini-cli
- codex-cli
---

# SKILL DE RISCO â€” AUDITOR DE RISCO EM LEILÃ•ES

## Overview

Analise de risco em leiloes de imoveis. Score 36 pontos, riscos juridicos/financeiros/operacionais, stress test 4 cenarios e ROI ponderado por risco.

## When to Use This Skill

- When the user mentions "risco leilao" or related topics
- When the user mentions "analise risco imovel leilao" or related topics
- When the user mentions "score risco leilao" or related topics
- When the user mentions "imovel seguro leilao" or related topics
- When the user mentions "stress test leilao" or related topics
- When the user mentions "roi ponderado leilao" or related topics

## Do Not Use This Skill When

- The task is unrelated to leiloeiro risco
- A simpler, more specific tool can handle the request
- The user needs general-purpose assistance without domain expertise

## How It Works

VocÃª Ã© um **Auditor de Risco SÃªnior** especializado em leilÃµes de imÃ³veis, com visÃ£o
integrada de riscos jurÃ­dicos, financeiros, operacionais e de mercado. Seu papel Ã©
mapear todos os riscos, quantificar os que podem ser quantificados e recomendar
a decisÃ£o de investimento.

---

## Categoria 1 â€” Riscos JurÃ­dicos

#### 1.1 Risco de Nulidade da ArremataÃ§Ã£o

| Risco | Probabilidade | Impacto | Score |
|-------|--------------|---------|-------|
| Falta de intimaÃ§Ã£o do cÃ´njuge | MÃ©dio | Muito Alto | ðŸ”´ |
| Edital publicado incorretamente | Baixo | Alto | ðŸŸ¡ |
| AvaliaÃ§Ã£o desatualizada (>12 meses) | MÃ©dio | MÃ©dio | ðŸŸ¡ |
| Bem impenhorÃ¡vel nÃ£o arguido | Baixo | Muito Alto | ðŸ”´ |
| Embargos com efeito suspensivo | Baixo | Muito Alto | ðŸ”´ |
| Processo com recursos pendentes | MÃ©dio | Alto | ðŸŸ¡ |
| CÃ´njuge sem meaÃ§Ã£o respeitada | Baixo | Alto | ðŸŸ¡ |

**Como mitigar:**
- Solicitar certidÃ£o dos autos (ou pesquisa no e-SAJ/PJE)
- Verificar se consta intimaÃ§Ã£o do cÃ´njuge
- Checar presenÃ§a de embargos via busca no sistema processual
- Confirmar publicaÃ§Ã£o do edital nos veÃ­culos exigidos

#### 1.2 Risco de Bem de FamÃ­lia

**Checklist de ExposiÃ§Ã£o:**
- [ ] Ã‰ o Ãºnico imÃ³vel do devedor? â†’ **Alto risco de bem de famÃ­lia**
- [ ] Devedor reside no imÃ³vel? â†’ **Alto risco**
- [ ] ImÃ³vel foi arguido como bem de famÃ­lia nos autos? â†’ **Verificar decisÃ£o judicial**
- [ ] ExecuÃ§Ã£o Ã© de crÃ©dito condominial ou tributÃ¡rio do prÃ³prio imÃ³vel? â†’ ExceÃ§Ã£o legal (pode penhorar)
- [ ] FianÃ§a locatÃ­cia? â†’ SÃºmula 549 STJ (pode penhorar â€” mas hÃ¡ divergÃªncia)

**DecisÃ£o:**
```
Se o imÃ³vel Ã‰ bem de famÃ­lia E a execuÃ§Ã£o NÃƒO Ã© de dÃ©bito do prÃ³prio imÃ³vel
ou crÃ©dito do art. 3Âº da Lei 8.009/90:
â†’ RISCO MUITO ALTO â€” NÃƒO ARREMATAR sem anÃ¡lise profunda dos autos
```

#### 1.3 Risco de Ã”nus Reais Ocultos

| Ã”nus | Como Detectar | Impacto |
|------|--------------|---------|
| Hipoteca anterior | CertidÃ£o de Ã´nus reais | Alto (pode retomar o imÃ³vel) |
| Usufruto vitalÃ­cio | MatrÃ­cula atualizada | Muito Alto (nÃ£o tem uso) |
| Penhora anterior | CertidÃ£o do distribuidor | MÃ©dio |
| ServidÃ£o | MatrÃ­cula | MÃ©dio (limita uso) |
| Aforamento (marinha) | MatrÃ­cula + SPU | MÃ©dio (laudÃªmio) |
| AÃ§Ã£o de usucapiÃ£o | Distribuidor | Alto (terceiro reivindica) |
| Promessa de compra e venda reg. | MatrÃ­cula | Alto |

**AÃ§Ã£o:** Sempre obter certidÃ£o

## Categoria 2 â€” Riscos Financeiros

#### 2.1 Risco de DÃ©bitos Acumulados

**Metodologia de CÃ¡lculo:**

```
IPTU:
  - Checar na prefeitura do municÃ­pio
  - Calcular dÃ©bito total (principal + multa 20% + juros 1% a.m.)
  - Prazo prescricional: 5 anos (CTN Art. 174)
  - Impacto: propter rem â€” arrematante paga

CONDOMÃNIO:
  - Solicitar ao sÃ­ndico/administradora extrato completo
  - Incluir: taxa condominial + multas + correÃ§Ã£o
  - Impacto: propter rem â€” arrematante paga (SÃºmula STJ 478)
  - AtenÃ§Ã£o: condomÃ­nio pode ter aÃ§Ã£o de cobranÃ§a paralela

ÃGUA/ESGOTO:
  - Verificar com concessionÃ¡ria (SABESP, CEDAE, Copasa etc.)
  - Pode gerar suspensÃ£o do serviÃ§o â€” custo de religaÃ§Ã£o
  - Em geral: dÃ­vida pessoal, nÃ£o propter rem (mas varia por estado)

ENERGIA ELÃ‰TRICA:
  - DÃ©bito pessoal (nÃ£o propter rem)
  - Verificar se hÃ¡ suspensÃ£o do serviÃ§o

TABELA RÃPIDA:
DÃ©bito estimado IPTU:          R$ ____________
DÃ©bito estimado CondomÃ­nio:    R$ ____________
DÃ©bito estimado Ãgua:          R$ ____________
Outros:                        R$ ____________
TOTAL DÃ‰BITOS:                 R$ ____________
```

#### 2.2 Risco de DesocupaÃ§Ã£o

**Estimativa de Custo por CenÃ¡rio:**

| CenÃ¡rio | Custo HonorÃ¡rios | Custo de Tempo | Prazo | Probabilidade |
|---------|-----------------|----------------|-------|---------------|
| Ocupante sai voluntariamente | R$ 0 | R$ 0 | 0-30 dias | 20-30% |
| NegociaÃ§Ã£o + ajuda de custo | R$ 3-10k | R$ 0 | 30-90 dias | 30-40% |
| AÃ§Ã£o de imissÃ£o sem resistÃªncia | R$ 5-15k | custo financ. | 3-6 meses | 20-30% |
| ImissÃ£o + recursos do devedor | R$ 10-30k | custo financ. | 6-18 meses | 10-20% |
| Processo longo + violÃªncia | R$ 20-50k | custo financ. | 12-36 meses | 5-10% |

**Custo financeiro do tempo (capital imobilizado):**
```
Capital imobilizado Ã— Taxa CDI Ã— Meses / 12
Exemplo: R$ 300.000 Ã— 10,5% Ã— 12 meses / 12 = R$ 31.500/ano (custo de oportunidade)
```

#### 2.3 Risco de Obra/Reforma

**Estimativas de Custo de Reforma (valores 2024):**

| Tipo de Reforma | Custo por mÂ² |
|----------------|---

## Categoria 3 â€” Riscos Operacionais

#### 3.1 Risco de NÃ£o Conseguir Finalizar a ArremataÃ§Ã£o

**ApÃ³s arrematar, o processo pode ser desfeito se:**

| Evento | Prazo para ocorrer | Probabilidade | ConsequÃªncia |
|--------|-------------------|---------------|-------------|
| Devedor paga antes da assinatura do auto | A qualquer momento antes | Baixo-MÃ©dio | LeilÃ£o desfeito, dinheiro devolvido |
| Embargos com efeito suspensivo | AtÃ© o auto de arremataÃ§Ã£o | Baixo | LeilÃ£o suspenso |
| Nulidade arguida no prazo de 10 dias | 10 dias apÃ³s arremataÃ§Ã£o | Baixo | AnulaÃ§Ã£o do leilÃ£o |
| Bem de famÃ­lia reconhecido tardiamente | ApÃ³s 10 dias â€” aÃ§Ã£o autÃ´noma | Muito Baixo | Complexa defesa |
| AÃ§Ã£o de embargos de terceiro | Qualquer momento (prazo prescricional) | Muito Baixo | Requer defesa judicial |

#### 3.2 Risco de Fraude ou ManipulaÃ§Ã£o

**Sinais de alerta em leilÃµes:**
- âš ï¸ Leiloeiro nÃ£o cadastrado na Junta Comercial
- âš ï¸ Plataforma online desconhecida sem CNPJ verificÃ¡vel
- âš ï¸ Valor de avaliaÃ§Ã£o muito incompatÃ­vel com mercado (extremos)
- âš ï¸ Edital publicado em prazo inferior ao legal
- âš ï¸ Lote com descriÃ§Ã£o vaga e sem matrÃ­cula informada
- âš ï¸ ExigÃªncia de depÃ³sito antes de visualizar documentos

**Como proteger:**
- Verificar leiloeiro no site da Junta Comercial do estado
- Confirmar o processo judicial no sistema do TJ (e-SAJ, PJE, SEEU)
- Nunca pagar sem confirmaÃ§Ã£o no processo judicial

---

## Categoria 4 â€” Riscos De Mercado E SistÃªmicos

#### 4.1 Risco de Liquidez no Momento da SaÃ­da

| CenÃ¡rio MacroeconÃ´mico | Impacto na Revenda |
|-----------------------|-------------------|
| Selic sobe mais (>14%) | CrÃ©dito encarece â†’ demanda cai â†’ demora mais |
| RecessÃ£o econÃ´mica | Mercado trava â†’ pode levar 2-3x mais tempo |
| Desemprego alto local | Comprador final some â†’ sem saÃ­da |
| Novo empreendimento vizinho | ConcorrÃªncia de novos â†’ pressÃ£o de preÃ§o |
| MudanÃ§a de zoneamento | Pode desvalorizar (ZEU vira residencial baixo) |
| Evento local negativo (crime, inundaÃ§Ã£o) | DesÃ¡gio adicional de 20-40% |

#### 4.2 Risco Ambiental e GeotÃ©cnico

**Verificar antes de arrematar:**
- [ ] ImÃ³vel em Ã¡rea de risco de deslizamento (CEMADEN)
- [ ] ImÃ³vel em Ã¡rea de inundaÃ§Ã£o (plano diretor municipal)
- [ ] ImÃ³vel em APP (Ãrea de PreservaÃ§Ã£o Permanente â€” margens de rios)
- [ ] ContaminaÃ§Ã£o do solo (Ã¡reas industriais, postos de gasolina)
- [ ] Laudo geotÃ©cnico de terrenos em encosta
- [ ] HistÃ³rico de sinistros (chuvas, enchentes) â€” INMET, prefeitura

**Fontes de consulta:**
- CEMADEN (cemaden.gov.br) â€” mapas de risco
- IBGE Malha Digital â€” zoneamento
- Prefeitura Municipal â€” alvarÃ¡, habite-se, plano diretor
- MDR/MCID â€” banco de dados de risco

---

## Preencher Para Cada Lote

```
RISCOS JURÃDICOS:
[ ] IntimaÃ§Ã£o cÃ´njuge confirmada?         Sim: 0 / NÃ£o: 3 / NÃ£o verificado: 2
[ ] Embargos com efeito suspensivo?       NÃ£o: 0 / Sim: 4
[ ] Bem de famÃ­lia provÃ¡vel?              NÃ£o: 0 / PossÃ­vel: 2 / ProvÃ¡vel: 4
[ ] Ã”nus reais verificados e ok?          Sim: 0 / NÃ£o verificado: 2 / Ã”nus grave: 4
[ ] DocumentaÃ§Ã£o regular?                 Sim: 0 / Irregular menor: 1 / Grave: 3

RISCOS FINANCEIROS:
[ ] DÃ©bitos IPTU + Cond. quantificados?   Sim (atÃ© 10% VMP): 0 / Altos (>10%): 2 / NÃ£o verificado: 2
[ ] SituaÃ§Ã£o da posse?                    Desocupado: 0 / Cooperativo: 1 / Litigioso: 3
[ ] Obras necessÃ¡rias?                    NÃ£o: 0 / Leves: 1 / Pesadas: 3

RISCOS OPERACIONAIS:
[ ] Leiloeiro verificado?                 Sim: 0 / NÃ£o: 2
[ ] Processo verificado no TJ?            Sim: 0 / NÃ£o: 2
[ ] Edital estÃ¡ completo?                 Sim: 0 / Incompleto: 2

RISCOS DE MERCADO:
[ ] Liquidez local?                       Alta: 0 / MÃ©dia: 1 / Baixa: 3
[ ] Risco ambiental?                      Baixo: 0 / MÃ©dio: 2 / Alto: 4

SCORE TOTAL: ___ / 36

CLASSIFICAÃ‡ÃƒO:
0-5:   BAIXO RISCO âœ… â€” Proceder com seguranÃ§a
6-10:  MÃ‰DIO RISCO âš ï¸ â€” Mitigar os pontos identificados
11-18: ALTO RISCO ðŸ”´ â€” SÃ³ com expertise e desconto maior
19+:   MUITO ALTO RISCO âŒ â€” Evitar, salvo especialista experiente
```

---

### ObrigatÃ³rias (Sempre, Para Qualquer Lote):

- [ ] CertidÃ£o de Ã´nus reais (matrÃ­cula atualizada) â€” R$ 50-150
- [ ] CertidÃ£o negativa de IPTU (ou extrato de dÃ©bitos)
- [ ] Leitura completa do edital (Bloco 1-8 da SKILL de Edital)
- [ ] Pesquisa do processo no sistema do TJ (ou cartÃ³rio)
- [ ] Verificar leiloeiro na Junta Comercial

### Complementares (Quando Score > 5):

- [ ] CertidÃ£o do distribuidor cÃ­vel (aÃ§Ãµes no imÃ³vel)
- [ ] Extrato de dÃ©bitos de condomÃ­nio
- [ ] Visita ao imÃ³vel ou Ã  rua (Google Street View no mÃ­nimo)
- [ ] Consulta ao sÃ­ndico sobre ocupaÃ§Ã£o e estado
- [ ] Extrato de dÃ©bitos de Ã¡gua/saneamento

## Para Lotes De Alto Valor (>R$ 500K):

- [ ] Pareceria com advogado especialista para anÃ¡lise dos autos
- [ ] Laudo de vistoria tÃ©cnica (engenheiro)
- [ ] Pesquisa de comparÃ¡veis com corretor CRECI local
- [ ] AnÃ¡lise de certidÃµes do devedor (fraude Ã  execuÃ§Ã£o)
- [ ] Consulta ao plano diretor municipal (uso e ocupaÃ§Ã£o do solo)

---

## Tomada De DecisÃ£o â€” Ãrvore De DecisÃ£o

```
SCORE DE RISCO:

â‰¤ 5 (BAIXO):
  â†’ ROI lÃ­quido > CDI? SIM â†’ ARREMATAR
  â†’ ROI lÃ­quido > CDI? NÃƒO â†’ AGUARDAR MELHOR OPORTUNIDADE

6-10 (MÃ‰DIO):
  â†’ Problemas sÃ£o mitigÃ¡veis? SIM + ROI > CDI+5% â†’ ARREMATAR com cautelas
  â†’ Problemas sÃ£o mitigÃ¡veis? NÃƒO â†’ NÃƒO ARREMATAR

11-18 (ALTO):
  â†’ VocÃª Ã© especialista? SIM + ROI > CDI+15% â†’ AVALIAR COM ADVOGADO
  â†’ VocÃª Ã© especialista? NÃƒO â†’ NÃƒO ARREMATAR

> 18 (MUITO ALTO):
  â†’ NÃƒO ARREMATAR (salvo casos excepcionais com assessoria)
```

---

---

## Risco De Itbi Sobre Vmp (NÃ£o Sobre O Lance)

**O problema:**
Muitos municÃ­pios cobram ITBI sobre o **valor venal de referÃªncia** (VMP), nÃ£o sobre
o valor efetivo da arremataÃ§Ã£o (lance). Isso aumenta o custo em atÃ© 3x.

**Exemplo:**
- ImÃ³vel arrematado por R$ 200.000
- Valor venal de referÃªncia (prefeitura): R$ 400.000
- ITBI 3% sobre lance: R$ 6.000
- ITBI 3% sobre venal: R$ 12.000 â† cobrado pela prefeitura

**Base legal para contestar:**
- STJ Tema 1.113: ITBI deve incidir sobre o valor efetivo da transaÃ§Ã£o
- Em leilÃ£o judicial: a carta de arremataÃ§Ã£o Ã© o tÃ­tulo â€” valor = lance
- Em leilÃ£o extrajudicial: a escritura com valor do lance Ã© o tÃ­tulo
- PossÃ­vel impugnar administrativamente ou via mandado de seguranÃ§a

**RecomendaÃ§Ã£o:** OrÃ§ar ITBI sobre VMP (cenÃ¡rio pessimista) e incluir no custo total.
Se conseguir pagar sobre o lance, Ã© economia extra.

## Risco De Ir Ganho De Capital Na Revenda

- O lucro na revenda Ã© tributado em 15% (atÃ© R$ 5M de ganho)
- Custo de aquisiÃ§Ã£o: valor do lance + ITBI + comissÃ£o + registro + obras documentadas
- IsenÃ§Ã£o: venda atÃ© R$ 440.000 do Ãºnico imÃ³vel a cada 5 anos
- IsenÃ§Ã£o: reinvestimento em outro imÃ³vel residencial em atÃ© 180 dias
- **Dica:** documentar TODAS as despesas com notas fiscais (reforma, regularizaÃ§Ã£o)
  para abater do ganho de capital

---

## O Arrematante EstÃ¡ Protegido?

**Regra geral (Art. 903, Â§5Âº CPC):**
A arremataÃ§Ã£o em hasta pÃºblica opera como aquisiÃ§Ã£o com proteÃ§Ã£o judicial.
O arrematante de boa-fÃ© Ã© protegido contra alienaÃ§Ãµes fraudulentas anteriores.

**Mas atenÃ§Ã£o aos cenÃ¡rios:**

| CenÃ¡rio | Risco para Arrematante | ProteÃ§Ã£o |
|---------|----------------------|----------|
| Devedor vendeu imÃ³vel antes da penhora | Muito Baixo | Art. 903 CPC protege arrematante |
| Terceiro alega ter comprado antes da penhora | MÃ©dio | Depende de registro + boa-fÃ© |
| ImÃ³vel objeto de aÃ§Ã£o de usucapiÃ£o por terceiro | Alto | Conflito de tÃ­tulos â€” pode anular |
| Devedor doou para parente (fraude contra credores) | Baixo | Arrematante em hasta protegido |

**VerificaÃ§Ã£o obrigatÃ³ria:**
- CertidÃ£o de distribuidor cÃ­vel: verificar se hÃ¡ aÃ§Ã£o real (usucapiÃ£o, reivindicatÃ³ria)
  movida por terceiro sobre o imÃ³vel
- Se existir aÃ§Ã£o de terceiro reivindicando o imÃ³vel: ALTO RISCO â€” evitar

---

## Como Fazer O Stress Test Do Investimento:

```
CENÃRIO OTIMISTA (probabilidade 20%):
  - Vende pelo VMP em 3 meses
  - Sem custos extras de desocupaÃ§Ã£o
  - ITBI sobre lance (nÃ£o sobre VMP)
  - ROI: ___ %

CENÃRIO BASE (probabilidade 50%):
  - Vende com 10% desconto sobre VMP em 6 meses
  - Custo de desocupaÃ§Ã£o negociado (R$ 5k)
  - ITBI sobre VMP
  - ROI: ___ %

CENÃRIO PESSIMISTA (probabilidade 25%):
  - Vende com 20% desconto sobre VMP em 12 meses
  - AÃ§Ã£o de imissÃ£o na posse (R$ 15k + 6 meses)
  - Reforma necessÃ¡ria (R$ 30k)
  - ROI: ___ %

CENÃRIO CATASTRÃ“FICO (probabilidade 5%):
  - ArremataÃ§Ã£o anulada (perda do sinal, mas dinheiro devolvido)
  - OU: nÃ£o consegue vender em 24 meses (capital travado)
  - OU: dÃ©bitos ocultos consomem a margem (condomÃ­nio alto)
  - ROI: ___ % (possivelmente negativo)

ROI PONDERADO (esperanÃ§a matemÃ¡tica):
= (ROI otimista Ã— 0,20) + (ROI base Ã— 0,50) + (ROI pessimista Ã— 0,25)
  + (ROI catastrÃ³fico Ã— 0,05)

Se ROI ponderado > CDI â†’ ARREMATAR
Se ROI ponderado < CDI â†’ NÃƒO VALE O RISCO
```

---

## GlossÃ¡rio De Riscos

| Termo | DefiniÃ§Ã£o |
|-------|-----------|
| Propter Rem | ObrigaÃ§Ã£o que segue o bem (IPTU, condomÃ­nio) â€” nÃ£o desaparece com a venda |
| Risco JurÃ­dico | Possibilidade de anulaÃ§Ã£o, nulidade ou impugnaÃ§Ã£o da arremataÃ§Ã£o |
| Risco Operacional | Dificuldade na execuÃ§Ã£o (desocupaÃ§Ã£o, reforma, regularizaÃ§Ã£o) |
| Risco TributÃ¡rio | ITBI sobre VMP vs. lance; IR sobre ganho de capital na revenda |
| Custo de Oportunidade | O que se deixa de ganhar ao imobilizar capital nesta operaÃ§Ã£o |
| Stress Test | SimulaÃ§Ã£o do pior cenÃ¡rio possÃ­vel para o investimento |
| Due Diligence | DiligÃªncia prÃ©via completa antes de arrematar |
| VaR (Value at Risk) | Perda mÃ¡xima estimada em cenÃ¡rio adverso |
| Margem de SeguranÃ§a | Buffer financeiro entre o custo total e o valor de mercado |
| Fraude Ã  ExecuÃ§Ã£o | AlienaÃ§Ã£o do bem apÃ³s a citaÃ§Ã£o para frustrar a execuÃ§Ã£o (Art. 792 CPC) |
| ROI Ponderado | Retorno esperado considerando probabilidade de cada cenÃ¡rio |

---

## InstalaÃ§Ã£o

Skill baseada em conhecimento (knowledge-only). NÃ£o requer instalaÃ§Ã£o de dependÃªncias.

```bash

## Verificar Se A Skill EstÃ¡ Registrada:

python C:\Users\renat\skills\agent-orchestrator\scripts\scan_registry.py
```

---

## Comandos E Uso

Como usar esta skill:

```bash

## Uso Via Orchestrator (AutomÃ¡tico):

python agent-orchestrator/scripts/match_skills.py "risco leilao imovel"

## "Score De Risco Dessa ArremataÃ§Ã£o"

```

---

## GovernanÃ§a

Esta skill implementa as seguintes polÃ­ticas de governanÃ§a:

- **action_log**: AnÃ¡lises de risco sÃ£o registradas pelo log_action para auditoria completa
- **rate_limit**: Controle via check_rate integrado ao ecossistema
- **requires_confirmation**: Score >28/36 (MUITO ALTO) gera confirmation_request obrigatÃ³rio
- **warning_threshold**: Score >21/36 (ALTO) dispara warning_threshold com alerta ao usuÃ¡rio

PolÃ­ticas adicionais:
- **ResponsÃ¡vel:** Ecossistema Leiloeiro IA
- **Escopo:** AnÃ¡lise e gestÃ£o de risco em leilÃµes de imÃ³veis
- **LimitaÃ§Ãµes:** Scores e classificaÃ§Ãµes sÃ£o indicativos. DecisÃ£o final Ã© do investidor.
- **Auditoria:** Validada por skill-sentinel
- **Dados sensÃ­veis:** NÃ£o armazena dados de risco do usuÃ¡rio

---

## ReferÃªncias

Fontes normativas e referÃªncias de risco:
- CEMADEN (cemaden.gov.br) â€” mapas de risco ambiental
- IBGE â€” malha digital e zoneamento
- CPC/2015 â€” Arts. 829-925 (ExecuÃ§Ã£o e ArremataÃ§Ã£o)
- Lei 9.514/1997 â€” AlienaÃ§Ã£o FiduciÃ¡ria
- Lei 8.009/1990 â€” Bem de FamÃ­lia
- STJ â€” jurisprudÃªncia consolidada sobre leilÃµes
- CTN Art. 130 â€” responsabilidade tributÃ¡ria propter rem

## Best Practices

- Provide clear, specific context about your project and requirements
- Review all suggestions before applying them to production code
- Combine with other complementary skills for comprehensive analysis

## Common Pitfalls

- Using this skill for tasks outside its domain expertise
- Applying recommendations without understanding your specific context
- Not providing enough project context for accurate analysis

## Related Skills

- `junta-leiloeiros` - Complementary skill for enhanced analysis
- `leiloeiro-avaliacao` - Complementary skill for enhanced analysis
- `leiloeiro-edital` - Complementary skill for enhanced analysis
- `leiloeiro-ia` - Complementary skill for enhanced analysis
- `leiloeiro-juridico` - Complementary skill for enhanced analysis

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.

