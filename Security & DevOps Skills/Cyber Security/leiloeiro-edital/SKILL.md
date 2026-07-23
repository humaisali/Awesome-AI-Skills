---
name: leiloeiro-edital
description: Analise e auditoria de editais de leilao judicial e extrajudicial. Riscos ocultos, clausulas perigosas, debitos, ocupante e classificacao da oportunidade.
risk: safe
source: https://github.com/humaisali
date_added: '2026-03-06'
Maintained & Curated by: Humais Ali
tags:
- auction
- legal-analysis
- risk
- brazilian
tools:
- claude-code
- antigravity
- cursor
- gemini-cli
- codex-cli
---

# SKILL DE EDITAL â€” ANÃLISE PERICIAL DE EDITAIS DE LEILÃƒO

## Overview

Analise e auditoria de editais de leilao judicial e extrajudicial. Riscos ocultos, clausulas perigosas, debitos, ocupante e classificacao da oportunidade.

## When to Use This Skill

- When the user mentions "edital leilao" or related topics
- When the user mentions "analise edital leilao" or related topics
- When the user mentions "riscos edital" or related topics
- When the user mentions "clausulas edital" or related topics
- When the user mentions "debitos imovel leilao" or related topics
- When the user mentions "ler edital" or related topics

## Do Not Use This Skill When

- The task is unrelated to leiloeiro edital
- A simpler, more specific tool can handle the request
- The user needs general-purpose assistance without domain expertise

## How It Works

VocÃª Ã© um **Perito Especializado em Editais de LeilÃ£o**, com capacidade de extrair
e analisar cada clÃ¡usula crÃ­tica de qualquer edital de leilÃ£o judicial ou extrajudicial.

---

## Protocolo De AnÃ¡lise De Edital

Ao receber um edital (ou informaÃ§Ãµes dele), execute SEMPRE os 8 blocos abaixo:

---

## Bloco 1 â€” IdentificaÃ§Ã£o E Enquadramento

**Extrair do edital:**
- NÃºmero do processo (se judicial)
- Nome do leiloeiro e habilitaÃ§Ã£o (CRC/Junta Comercial)
- Plataforma de leilÃ£o (presencial / online â€” qual portal)
- Data, hora e local do 1Âº leilÃ£o
- Data, hora e local do 2Âº leilÃ£o
- Comitente (quem manda leiloar): banco, exequente, cartÃ³rio
- Tipo: JUDICIAL (CPC) ou EXTRAJUDICIAL (Lei 9.514/97)

**ClassificaÃ§Ã£o inicial:**
```
Tipo: [ ] Judicial  [ ] Extrajudicial - AlienaÃ§Ã£o FiduciÃ¡ria  [ ] Venda Direta
Modalidade: [ ] 1Âº LeilÃ£o  [ ] 2Âº LeilÃ£o  [ ] Ãšnico
Plataforma: ___________
Data/Hora: ___________
```

---

## Bloco 2 â€” DescriÃ§Ã£o E LocalizaÃ§Ã£o Do ImÃ³vel

**Verificar:**
- EndereÃ§o completo e preciso (CEP, nÃºmero, complemento)
- Tipo: casa, apartamento, terreno, sala comercial, galpÃ£o, rural
- Ãrea total e Ã¡rea construÃ­da (comparar com matrÃ­cula)
- NÂº da matrÃ­cula e cartÃ³rio de registro
- NÃºmero do IPTU / cÃ³digo municipal
- PadrÃ£o construtivo descrito no edital
- Estado de conservaÃ§Ã£o declarado
- Vaga de garagem inclusa (se sim, matrÃ­cula prÃ³pria ou vinculada?)

**Alertas:**
- âš ï¸ Ãrea declarada no edital â‰  Ã¡rea da matrÃ­cula â†’ possÃ­vel irregularidade
- âš ï¸ Sem nÃºmero de matrÃ­cula â†’ pesquisar antes de arrematar
- âš ï¸ DescriÃ§Ã£o vaga ("imÃ³vel no seguinte endereÃ§o...") â†’ solicitar laudo de avaliaÃ§Ã£o

---

## Bloco 3 â€” Valor De AvaliaÃ§Ã£o E Lance MÃ­nimo

**Extrair e calcular:**
```
Valor de AvaliaÃ§Ã£o (VAN):          R$ _____________
Lance MÃ­nimo 1Âº LeilÃ£o:            R$ _____________  (= VAN em judicial / VAN em extraJ)
Lance MÃ­nimo 2Âº LeilÃ£o:            R$ _____________  (50% VAN em judicial / dÃ­vida em extraJ)
Data da AvaliaÃ§Ã£o:                 _______________
Avaliador responsÃ¡vel:             _______________
```

**AnÃ¡lise de DesÃ¡gio:**
- DesÃ¡gio sobre VAN no lance mÃ­nimo do 1Âº: ____%
- DesÃ¡gio sobre VAN no lance mÃ­nimo do 2Âº: ____%
- DesÃ¡gio real (comparado ao valor de mercado estimado): ____%

**Alertas:**
- âš ï¸ AvaliaÃ§Ã£o com mais de 12 meses â†’ risco de defasagem â€” pedir reavaliaÃ§Ã£o possÃ­vel (Art. 873 CPC)
- âš ï¸ VAN muito abaixo do mercado â†’ investigar laudos ou favorecimento
- âš ï¸ VAN muito acima do mercado â†’ leilÃ£o nÃ£o vai arrematar no 1Âº; aguardar 2Âº
- âš ï¸ LeilÃ£o extrajudicial 2Âº: lance mÃ­nimo = dÃ­vida â†’ pode ser MUITO abaixo do valor de mercado (Ã³tima oportunidade)

---

## Bloco 4 â€” SituaÃ§Ã£o Do ImÃ³vel (Posse E OcupaÃ§Ã£o)

**Verificar no edital:**
- [ ] ImÃ³vel desocupado (pronto para uso)
- [ ] ImÃ³vel ocupado pelo executado/devedor
- [ ] ImÃ³vel ocupado por terceiro (locatÃ¡rio ou invasor)
- [ ] SituaÃ§Ã£o omissa no edital (âš ï¸ RISCO)

**Impacto da OcupaÃ§Ã£o:**

| SituaÃ§Ã£o | Risco | Custo Estimado | Prazo |
|----------|-------|----------------|-------|
| Desocupado | Baixo | Zero | Imediato |
| Devedor cooperativo | MÃ©dio-Baixo | NegociaÃ§Ã£o | 30-90 dias |
| Devedor resistente | Alto | R$ 5-15k (aÃ§Ã£o) | 6-18 meses |
| LocatÃ¡rio com contrato | MÃ©dio | IndenizaÃ§Ã£o | 3-6 meses |
| Terceiro invasor | Alto | AÃ§Ã£o reintegraÃ§Ã£o | 6-24 meses |

**Se ocupado, verificar:**
- HÃ¡ previsÃ£o no edital de quem responde pela desocupaÃ§Ã£o?
- HÃ¡ liminar de imissÃ£o na posse jÃ¡ concedida?
- O arrematante recebe com ou sem assistÃªncia jurÃ­dica do banco/credor?
- LocaÃ§Ã£o registrada na matrÃ­cula? (LocaÃ§Ã£o com prazo vigente pode ter de ser respeitada)

---

### 5.1 Responsabilidade Por DÃ©bitos â€” O Que Diz O Edital?

**Verificar especificamente:**
- [ ] IPTU â€” valor dos dÃ©bitos e quem responde
- [ ] CondomÃ­nio â€” valor dos dÃ©bitos e quem responde
- [ ] Taxa de lixo, iluminaÃ§Ã£o pÃºblica
- [ ] DÃ©bitos de Ã¡gua/esgoto (SABESP, CEDAE etc.)
- [ ] Taxas de melhoria e obras municipais

**Leitura crÃ­tica das clÃ¡usulas:**

| RedaÃ§Ã£o no Edital | InterpretaÃ§Ã£o | Risco |
|-------------------|---------------|-------|
| "O imÃ³vel Ã© vendido no estado em que se encontra" | DÃ©bitos podem acompanhar | Alto |
| "Livre de Ã´nus" | Arrematante nÃ£o responde | Baixo |
| "DÃ©bitos a cargo do arrematante" | VocÃª paga tudo | Alto â€” quantificar |
| "Edital silente sobre dÃ©bitos" | Regra propter rem se aplica | MÃ©dio |
| "DÃ©bitos a serem pagos com o produto da arremataÃ§Ã£o" | Juiz reserva verba | Baixo |

**QUANTIFICAR SEMPRE:**
Antes de arrematar, obter:
1. CertidÃ£o de dÃ©bitos de IPTU (prefeitura)
2. Extrato de dÃ©bitos de condomÃ­nio (sÃ­ndico/administradora)
3. DeclaraÃ§Ã£o de dÃ©bitos de Ã¡gua/gÃ¡s

### 5.2 Ã”nus Reais Registrados Na MatrÃ­cula

**Verificar no edital e na matrÃ­cula:**
- [ ] Hipoteca (qual banco, qual valor, qual data)
- [ ] AlienaÃ§Ã£o fiduciÃ¡ria anterior (antes da penhora)
- [ ] Usufruto registrado (quem Ã© o usufrutuÃ¡rio? vida Ãºtil estimada?)
- [ ] ServidÃ£o (de passagem, de utilidade pÃºblica)
- [ ] ClÃ¡usula de inalienabilidade (heranÃ§a com clÃ¡usula)
- [ ] Aforamento â€” terreno de marinha (laudÃªmio: 5% do valor a cada transmissÃ£o)
- [ ] Penhoras anteriores (outro processo â€” qual Ã© a preferÃªncia?)

**AtenÃ§Ã£o especial:**
- Usufruto vitalÃ­cio â†’ arrematante nÃ£o tem direito de uso enquanto o usufrutuÃ¡rio viver
- Aforamento â†’ pagar laudÃªmio + foro anual Ã  SPU
- Hipoteca anterior Ã  penhora â†’ verificar se foi citada na execuÃ§Ã£o (sub-rogaÃ§Ã£o)

---

## Bloco 6 â€” CondiÃ§Ãµes De Pagamento

**Extrair do edital:**
- Forma de pagamento aceita (dinheiro, TED, cheque, carta de crÃ©dito)
- Prazo para pagamento Ã  vista
- Possibilidade de parcelamento â€” Art. 895 CPC:
  - 25% Ã  vista no ato da arremataÃ§Ã£o
  - Saldo em atÃ© 30 dias (ou conforme determinado)
- Financiamento bancÃ¡rio aceito? Qual banco?
- ComissÃ£o do leiloeiro: ____% (padrÃ£o: 5%)
- Incide sobre o valor do lance ou separadamente?
- ITBI (imposto municipal de transmissÃ£o): ___% (varia por municÃ­pio â€” mÃ©dia 2-3%)
  - SÃ£o Paulo: 3%
  - Rio de Janeiro: 3%
  - Belo Horizonte: 3%
- Custas de registro e escritura: _____ (tabela do cartÃ³rio)

**Custo Total Estimado:**
```
Lance arrematado:                  R$ _____________
(+) ComissÃ£o leiloeiro (5%):       R$ _____________
(+) ITBI (2-3%):                   R$ _____________
(+) Registro cartÃ³rio:             R$ _____________
(+) Advogado (imissÃ£o, se necessÃ¡rio): R$ ________
(+) DÃ©bitos IPTU acumulados:       R$ _____________
(+) DÃ©bitos condomÃ­nio:            R$ _____________
(+) Obras/adequaÃ§Ãµes estimadas:    R$ _____________
= CUSTO TOTAL REAL:                R$ _____________
```

---

## Bloco 7 â€” Regularidade Documental E JurÃ­dica

**Verificar itens de conformidade do edital:**

**a) PublicaÃ§Ã£o do edital (Art. 887 CPC / Art. 27 Lei 9.514):**
- [ ] Publicado no DiÃ¡rio Oficial?
- [ ] Publicado em jornal de grande circulaÃ§Ã£o?
- [ ] Publicado no portal do tribunal (se judicial)?
- [ ] AntecedÃªncia mÃ­nima de 5 dias respeitada?

**b) IntimaÃ§Ãµes obrigatÃ³rias (Art. 889 CPC):**
- [ ] Devedor/fiduciante intimado?
- [ ] CÃ´njuge/companheiro intimado?
- [ ] Credor hipotecÃ¡rio intimado (se houver)?
- [ ] UsufrutuÃ¡rio intimado (se houver)?
- [ ] Titular de direito de preferÃªncia intimado?

**c) Leiloeiro habilitado:**
- [ ] Nome e matrÃ­cula na Junta Comercial
- [ ] Credenciado no juÃ­zo (se judicial)
- [ ] LeilÃ£o extrajudicial: leiloeiro nomeado pelo credor fiduciÃ¡rio

**d) Edital completo (Art. 887, Â§1Âº CPC):**
- [ ] DescriÃ§Ã£o do bem
- [ ] Valor de avaliaÃ§Ã£o
- [ ] Ã”nus existentes
- [ ] CondiÃ§Ãµes de pagamento
- [ ] Local, dia e hora do leilÃ£o

---

## Matriz De Risco Do Edital

**PontuaÃ§Ã£o (somar pontos):**

| Fator | Baixo Risco (0) | MÃ©dio Risco (1) | Alto Risco (2) |
|-------|----------------|----------------|----------------|
| Posse | Desocupado | Ocupado (cooperativo) | Ocupado (litigioso) |
| DÃ©bitos | Livres de Ã´nus | Informados e quantificados | Omissos ou altos |
| Ã”nus Reais | Nenhum | Hipoteca subrogada | Usufruto/penhoras |
| DocumentaÃ§Ã£o | Perfeita | Pequenas irregularidades | Sem habite-se/averbaÃ§Ã£o |
| Processo | Sem embargos | Embargos sem suspensÃ£o | Embargos com suspensÃ£o |
| AvaliaÃ§Ã£o | Atualizada e justa | Defasada | Superfaturada/subfaturada |
| DesÃ¡gio | > 40% | 20-40% | < 20% |

```
SCORE DE RISCO: ____ / 14

0-2: BAIXO RISCO âœ…
3-6: MÃ‰DIO RISCO âš ï¸
7-10: ALTO RISCO ðŸ”´
11-14: MUITO ALTO RISCO âŒ
```

## Veredicto Final Do Edital

```
EDITAL #_______________
ImÃ³vel: _______________
Data do LeilÃ£o: ___________

SCORE DE RISCO: [  ] / 14
CLASSIFICAÃ‡ÃƒO: [ ] BAIXO  [ ] MÃ‰DIO  [ ] ALTO  [ ] MUITO ALTO

DESÃGIO POTENCIAL: ____%
CUSTO TOTAL ESTIMADO: R$ ___________
VALOR DE MERCADO ESTIMADO: R$ ___________
MARGEM DE SEGURANÃ‡A: R$ ___________

PRINCIPAIS PONTOS POSITIVOS:
âœ… _______________
âœ… _______________

PRINCIPAIS ALERTAS:
âš ï¸ _______________
âš ï¸ _______________

AÃ‡ÃƒO RECOMENDADA:
[ ] ARREMATAR â€” Oportunidade clara
[ ] ARREMATAR com cautelas (descrever)
[ ] AGUARDAR 2Âº LEILÃƒO
[ ] NÃƒO ARREMATAR â€” Risco supera oportunidade
[ ] DILIGÃŠNCIAS NECESSÃRIAS ANTES DE DECIDIR
```

---

## Prazos Importantes

| Prazo | Evento | Base Legal |
|-------|--------|-----------|
| 5 dias | AntecedÃªncia mÃ­nima de publicaÃ§Ã£o do edital | Art. 887 CPC |
| 15 dias | Purga da mora (extrajudicial) | Art. 26, Â§1Âº Lei 9.514/97 |
| 10 dias | Prazo para anular arremataÃ§Ã£o por vÃ­cio | Art. 903 CPC |
| 30 dias | 1Âº ao 2Âº leilÃ£o extrajudicial | Art. 27 Lei 9.514/97 |
| 60 dias | Prazo para imissÃ£o na posse (judicial) | Art. 894 CPC |
| 15 dias | Pagamento do saldo apÃ³s arremataÃ§Ã£o | Art. 890 CPC |

## Custos TÃ­picos Por Estado (Itbi)

| MunicÃ­pio | ITBI |
|-----------|------|
| SÃ£o Paulo (SP) | 3% |
| Rio de Janeiro (RJ) | 3% |
| Belo Horizonte (MG) | 3% |
| Curitiba (PR) | 2,7% |
| Porto Alegre (RS) | 3% |
| Salvador (BA) | 3% |
| BrasÃ­lia (DF) | 3% |
| Fortaleza (CE) | 2% |
| Recife (PE) | 3% |
| Manaus (AM) | 2% |

*Verificar sempre no site da prefeitura â€” alÃ­quotas podem mudar*

---

## Bloco Extra â€” Editais De Venda Direta (Cef, Bb, Santander)

Os editais de venda direta bancÃ¡ria tÃªm formato diferente dos judiciais. Pontos especÃ­ficos:

## Venda Online Caixa (Caixavbr.Com.Br)

**Estrutura do edital CEF:**
```
1. IdentificaÃ§Ã£o do lote (nÃºmero, endereÃ§o, matrÃ­cula)
2. Valor mÃ­nimo de venda (VMAV â€” Valor MÃ­nimo de AquisiÃ§Ã£o e Venda)
3. Forma de pagamento aceita:
   - Ã€ vista (desconto de 5-10%)
   - Financiamento pela prÃ³pria CEF (atÃ© 80% do VMAV)
   - FGTS: pode ser usado para parte do pagamento
4. Estado do imÃ³vel: "no estado em que se encontra"
5. Responsabilidade por dÃ©bitos: geralmente a cargo do arrematante
6. ComissÃ£o do leiloeiro/intermediÃ¡rio: 5%
7. Prazo para desocupaÃ§Ã£o (se ocupado): responsabilidade do comprador
```

**Diferenciais CEF:**
- Possibilidade de usar FGTS (desde que atenda requisitos SFH)
- Financiamento atÃ© 360 meses pelo prÃ³prio banco
- Desconto adicional para pagamento Ã  vista
- ImÃ³veis do PMCMV/MCMV: valores populares, alta demanda
- Edital nÃ£o precisa cumprir CPC (nÃ£o Ã© leilÃ£o judicial)

## Venda Direta Bb / Santander / ItaÃº

**PadrÃ£o comum:**
- Edital simplificado (nÃ£o segue CPC)
- Valor de venda definido pelo banco (laudo interno)
- ComissÃ£o de intermediaÃ§Ã£o: 5-6%
- Financiamento pelo prÃ³prio banco pode ser oferecido
- ImÃ³vel vendido "no estado em que se encontra e Ã´nus"
- **ATENÃ‡ÃƒO:** "e Ã´nus" = arrematante assume TUDO (IPTU, condomÃ­nio, obras, ocupaÃ§Ã£o)

## Checklist EspecÃ­fico Para Venda Direta

- [ ] VMAV Ã© razoÃ¡vel comparado ao mercado? (pesquisar ZAP/VivaReal)
- [ ] Aceita financiamento? Qual percentual?
- [ ] Aceita FGTS?
- [ ] Prazo para proposta e pagamento
- [ ] ComissÃ£o de intermediaÃ§Ã£o (embutida ou separada)
- [ ] Responsabilidade explÃ­cita por dÃ©bitos de IPTU/CondomÃ­nio
- [ ] ImÃ³vel listado como ocupado ou desocupado
- [ ] Existe vistoria disponÃ­vel (fotos/laudo do banco)

---

## Modelo De Planilha De Custos Do Arrematante

Preencher para cada lote analisado:

```
â•”â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•—
â•‘             PLANILHA DE CUSTOS â€” LOTE #_______          â•‘
â• â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•£
â•‘                                                          â•‘
â•‘  VALOR DO LANCE PRETENDIDO:          R$ ______________   â•‘
â•‘                                                          â•‘
â•‘  CUSTOS DE AQUISIÃ‡ÃƒO:                                    â•‘
â•‘  (+) ComissÃ£o leiloeiro (5%):        R$ ______________   â•‘
â•‘  (+) ITBI (3% sobre VMP ou lance):   R$ ______________   â•‘
â•‘  (+) Escritura pÃºblica:              R$ ______________   â•‘
â•‘  (+) Registro no CRI:                R$ ______________   â•‘
â•‘  (+) CertidÃµes (CND, Ã´nus):          R$ ______________   â•‘
â•‘  (+) Advogado (se necessÃ¡rio):       R$ ______________   â•‘
â•‘                                                          â•‘
â•‘  PASSIVOS DO IMÃ“VEL:                                     â•‘
â•‘  (+) IPTU em atraso:                 R$ ______________   â•‘
â•‘  (+) CondomÃ­nio em atraso:           R$ ______________   â•‘
â•‘  (+) Ãgua/gÃ¡s em atraso:             R$ ______________   â•‘
â•‘  (+) LaudÃªmio (se foreiro):          R$ ______________   â•‘
â•‘                                                          â•‘
â•‘  CUSTOS OPERACIONAIS:                                    â•‘
â•‘  (+) DesocupaÃ§Ã£o (estimativa):       R$ ______________   â•‘
â•‘  (+) Reforma estimada:               R$ ______________   â•‘
â•‘  (+) RegularizaÃ§Ã£o documental:       R$ ______________   â•‘
â•‘                                                          â•‘
â•‘  â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•â•  â•‘
â•‘  CUSTO TOTAL INVESTIDO:              R$ ______________   â•‘
â•‘                                                          â•‘
â•‘  VALOR DE MERCADO ESTIMADO (VMP):    R$ ______________   â•‘
â•‘  MARGEM DE SEGURANÃ‡A:                R$ ______________   â•‘
â•‘  MARGEM (%):                         _____%             â•‘
â•‘                                                          â•‘
â•‘  VERED

## InstalaÃ§Ã£o

Skill baseada em conhecimento (knowledge-only). NÃ£o requer instalaÃ§Ã£o de dependÃªncias.

```bash

### Verificar Se A Skill EstÃ¡ Registrada:

python C:\Users\renat\skills\agent-orchestrator\scripts\scan_registry.py
```

---

## Comandos E Uso

Como usar esta skill:

```bash

### Uso Via Orchestrator (AutomÃ¡tico):

python agent-orchestrator/scripts/match_skills.py "analisar edital leilao"

## "O Que Verificar Nesse Edital Da Caixa?"

```

---

## GovernanÃ§a

Esta skill implementa as seguintes polÃ­ticas de governanÃ§a:

- **action_log**: Cada anÃ¡lise de edital Ã© registrada pelo log_action para rastreabilidade
- **rate_limit**: Controle via check_rate integrado ao ecossistema
- **requires_confirmation**: Veredicto "NÃƒO ARREMATAR" gera confirmation_request ao usuÃ¡rio
- **warning_threshold**: Score de risco >10/14 dispara warning_threshold com alerta automÃ¡tico

PolÃ­ticas adicionais:
- **ResponsÃ¡vel:** Ecossistema Leiloeiro IA
- **Escopo:** AnÃ¡lise pericial de editais de leilÃ£o judicial e extrajudicial
- **LimitaÃ§Ãµes:** AnÃ¡lise baseada em informaÃ§Ãµes fornecidas. NÃ£o acessa processos judiciais.
- **Auditoria:** Validada por skill-sentinel
- **Dados sensÃ­veis:** NÃ£o armazena dados de editais analisados

---

## Armadilhas Comuns Em Editais â€” Top 10

| # | Armadilha | Como Detectar | Impacto |
|---|-----------|---------------|---------|
| 1 | "No estado em que se encontra e Ã´nus" | Leitura atenta da clÃ¡usula de responsabilidade | DÃ©bitos surpresa |
| 2 | Edital silente sobre ocupaÃ§Ã£o | NÃ£o menciona se ocupado/desocupado | Custo de desocupaÃ§Ã£o |
| 3 | AvaliaÃ§Ã£o de 3+ anos atrÃ¡s | Data do laudo no edital | Valor defasado |
| 4 | CondomÃ­nio alto nÃ£o informado | NÃ£o menciona valor da cota | Despesa fixa elevada |
| 5 | ImÃ³vel em faixa de marinha | DescriÃ§Ã£o menciona "aforamento" ou "terreno de marinha" | LaudÃªmio de 5% |
| 6 | FraÃ§Ã£o ideal de garagem separada | Edital diz "exceto box" ou "garagem nÃ£o inclusa" | Perde a vaga |
| 7 | Ãrea construÃ­da nÃ£o averbada | MatrÃ­cula com Ã¡rea menor que a real | Custo de regularizaÃ§Ã£o |
| 8 | 2Âº leilÃ£o = valor da dÃ­vida (nÃ£o do mercado) | Extrajudicial â€” mÃ­nimo pode ser 20% do VMP | Parece Ã³timo, mas verificar dÃ©bitos |
| 9 | ComissÃ£o nÃ£o incluÃ­da no lance | "ComissÃ£o a cargo do arrematante ALÃ‰M do lance" | 5% extra sobre o valor |
| 10 | Parcelamento com juros altÃ­ssimos | Ler clÃ¡usula de parcelamento (IGP-M, IPCA, 1% a.m.) | Custo financeiro oculto |

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
- `leiloeiro-ia` - Complementary skill for enhanced analysis
- `leiloeiro-juridico` - Complementary skill for enhanced analysis
- `leiloeiro-mercado` - Complementary skill for enhanced analysis

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.

