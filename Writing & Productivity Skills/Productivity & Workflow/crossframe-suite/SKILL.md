---
name: crossframe-suite
description: "Use when the user explicitly invokes CrossFrame Suite for Chinese structural diagnosis workflows across relationships, organizations, public issues, philosophy, research, or essay output."
category: workflow
risk: safe
source: https://github.com/humaisali
source_repo: xi-kari/crossframe-skill
source_type: community
date_added: 2026-06-16
Maintained & Curated by: Humais Ali
license: MIT
license_source: https://github.com/humaisali
tools:
  - "Agent Skills"
  - Codex
  - Claude
tags:
  - crossframe
  - chinese
  - workflow
  - multi-skill
  - structural-diagnosis
---
# CrossFrame Suite


## When to Use This Skill

- Use only when the user explicitly names CrossFrame Suite, `crossframe-suite`, `/crossframe-suite`, or `$crossframe-suite`.
- Use as the umbrella router when a CrossFrame task may need multiple sibling skills, such as diagnosis plus public analysis, essay output, and review.
- Do not load every sibling skill by default; follow the routed workflow and progressive-reading rules in the original body below.

## Packaged Source Note

This AAS-ready copy preserves the original CrossFrame skill body below. Chinese remains the canonical semantic layer; English metadata is only for discovery, installation, and repository review.

## Limitations

- The skill body is intentionally Chinese-canonical; English metadata is for discovery and does not replace the original Chinese terms.
- Use only after explicit CrossFrame invocation or `crossframe-suite` routing; do not apply it as a generic default reasoning layer.
- It structures analysis, drafting, and review, but does not replace source verification, domain expertise, or legal, medical, or financial judgment.

`crossframe-suite` æ˜¯æ€»è°ƒåº¦ skillï¼Œä¸æ›¿ä»£ä»»ä½•ä¸“é¡¹ skillã€‚å®ƒåªåšä¸‰ä»¶äº‹ï¼š

1. åˆ¤æ–­ç”¨æˆ·ä»»åŠ¡å±žäºŽå“ªæ¡å·¥ä½œæµã€‚
2. å®‰æŽ’è¿žç»­è¯»å–é¡ºåºã€‚
3. è¾“å‡ºä¸€ä¸ªç®€çŸ­çš„è°ƒåº¦æçº²ï¼Œç„¶åŽè¿›å…¥ç›¸åº” skillã€‚

å®ƒä¸å¤åˆ¶ `crossframe`ã€`crossframe-essay` æˆ–å…¶å®ƒå¹³è¡Œ skill çš„æ­£æ–‡ã€‚ä¸­æ–‡ä¸ºæƒå¨è¯­ä¹‰ï¼›è‹±æ–‡åªä½œ skill idã€æ–‡ä»¶åå’Œå¯¹å¤–ä¼ æ’­åã€‚

å½“ä»»åŠ¡è§¦å‘ CrossFrame ä¸»ä½“æ—¶ï¼Œsuite è¿˜è¦æŠŠ `../crossframe/references/runtime-read-policy.md` ä¸Ž `../crossframe/references/continuity-closure-map.md` çº³å…¥è°ƒåº¦åˆ¤æ–­ï¼šæœ¬æ¬¡æ˜¯å¦éœ€è¦æŒ‰ v5.0 åŽŸæ–‡è¿žç»­æ¿å—è”è¯»ï¼Œè€Œä¸æ˜¯åªè¯»å•ä¸ªæ¦‚å¿µå¡ã€‚éœ€è¦åŒ…è¯´æ˜Žæˆ–æºé”šç‚¹æ—¶ï¼Œå†ç”±ä¸‹æ¸¸å®šå‘è¯»å– `continuity-bundles.md` æˆ–å…·ä½“åŒ…æ–‡ä»¶ã€‚v3.0 ä¸Ž v2.0 æ–‡ä»¶åªä½œä¸ºåŽ†å²åŸºçº¿ï¼›é»˜è®¤ä»¥ v5.0 æºç»“æž„ä¸ºå‡†ã€‚

suite å…¥å£çš„äº¤äº’é€‰æ‹©åªç¡®è®¤ä¸¤é¡¹ï¼šè¾“å‡ºæ¨¡å¼ä¸Žè§’è‰²ã€‚æ–‡ç« ç±»åž‹ä¸åœ¨ suite å¼€å¤´é€‰æ‹©ï¼›è‹¥æœ€ç»ˆè¿›å…¥ `crossframe-essay` ä¸”æ–‡ç« å±‚æœªå…³é—­ï¼Œå…ˆå®Œæˆé—®é¢˜æ‹†è§£ä¸Žç»“æž„æ´žå¯Ÿåº•ç¨¿ï¼Œå†ç”± `crossframe-essay/templates/article-type-selection-dialog.md` åœ¨æ­£æ–‡ç”Ÿæˆå‰å•ç‹¬ç¡®è®¤ã€‚

## æ˜¾å¼è°ƒç”¨åŽçš„æ€»å…¥å£

åªæœ‰ç”¨æˆ·æ˜¾å¼è°ƒç”¨ `crossframe-suite`ã€`$crossframe-suite`ã€`/crossframe-suite` æˆ–æ˜Žç¡®è¦æ±‚ä½¿ç”¨ CrossFrame Suite æ—¶ï¼Œæ‰ä»Žæœ¬ skill è¿›å…¥ã€‚è¿›å…¥ä¹‹åŽï¼Œä¼˜å…ˆç”±æœ¬ skill è°ƒåº¦ï¼›åªæœ‰ä»»åŠ¡éžå¸¸å•ä¸€ä¸”ç”¨æˆ·ç‚¹åäº†ä¸“é¡¹ skill æ—¶ï¼Œæ‰ç›´æŽ¥ä½¿ç”¨å¯¹åº”ä¸“é¡¹ skillã€‚

å½“ç”¨æˆ·é€šè¿‡æœ¬ skill ä½œä¸ºæ€»å…¥å£æå‡ºä»»ä½• CrossFrame å†…å®¹ä»»åŠ¡æ—¶ï¼Œé»˜è®¤æœ€ç»ˆéƒ½ç”Ÿæˆ**5.0 æ··åˆé•¿æ–‡**ï¼Œè¾“å‡ºæ¡£ä½ä¸º `full-visible-v5-longform`ï¼šå®Œæ•´å¯è§åº•ç¨¿ + å®Œæ•´é•¿æ–‡æ­£æ–‡ã€‚ä¸“é¡¹äº§ç‰©å¯ä»¥å…ˆç”Ÿæˆï¼Œä½†æœ€åŽé»˜è®¤è¿›å…¥æ–‡ç« å±‚ã€‚

```text
crossframe -> [needed sibling skills] -> crossframe-essay(full-visible-v5-longform) -> crossframe-review
```

è¿™æ¡é»˜è®¤ä¸æ˜¯ä¸ºäº†æŠŠæ‰€æœ‰å›žç­”å†™é•¿ï¼Œè€Œæ˜¯å› ä¸ºæ–‡ç« æ›´é€‚åˆæŠŠç»“æž„åˆ¤æ–­ã€ä¸“é¡¹äº§ç‰©å’Œ v5.0 ä¿çœŸæ£€æŸ¥äº¤ç»™æ™®é€šè¯»è€…ï¼šå…ˆå®Œæˆå¿…è¦çš„è¯Šæ–­/è¯„å®¡/æ¡ˆä¾‹/æ•™å­¦/è¾©è®º/å¤‡å¿˜å½•ï¼Œå†å½¢æˆåº•ç¨¿ï¼Œå†æˆæ–‡ï¼Œæœ€åŽè¿‡è´¨é‡é—¸ã€‚

å®Œæ•´äº¤äº’é¡ºåºå›ºå®šä¸ºï¼š`/crossframe-suite -> æ¨¡å¼/è§’è‰²é€‰æ‹©å™¨(4+6) -> suite è·¯ç”±ä¸Žä¸“é¡¹æ‹†è§£ -> ç»“æž„æ´žå¯Ÿåº•ç¨¿ -> æ–‡ç« ç±»åž‹é€‰æ‹©å™¨ -> å†™ä½œæŠ€æ³•è¯»å– -> æ–‡ç« æ­£æ–‡ -> è´¨é‡é—¸æ”¶æŸ`ã€‚æ–‡ç« ç±»åž‹é€‰æ‹©å™¨å¿…é¡»å‘ç”Ÿåœ¨ç»“æž„æ´žå¯Ÿåº•ç¨¿ä¹‹åŽã€æ–‡ç« æ­£æ–‡ä¹‹å‰ã€‚

è¿™æ¡é»˜è®¤ä¸ç›´æŽ¥æŠŠå›ºå®šå£°å£ä¼ ç»™ `crossframe-essay`ã€‚å£°å£ç”± `references/output-mode-selector.md` ä¸­çš„è§’è‰²ã€è¾“å‡ºæ¨¡å¼ä¸Ž `topic_sensitivity` å…±åŒå†³å®šï¼šå­¦æœ¯ä¸“å®¶/æ‰¹åˆ¤åæ€è€…é»˜è®¤ä¸­æ€§åˆ†æžä½“ï¼Œå¤§ä¼—ä¼ æ’­/æœªæ¥æŽ¢ç´¢è€…å¯å¯ç”¨ç¼–è¾‘åº•è‰²ï¼›ç”¨æˆ·æ˜¾å¼è¦æ±‚â€œäº²åˆ‡/ç¼–è¾‘å£å»/ç­”å¤ä½“â€æ—¶è¦†ç›–ã€‚ä¸­æ€§åˆ†æžä½“ä¸æ˜¯å†·æ·¡ä½“ï¼Œ`vulnerable` ä¸»é¢˜ä»è¦å…ˆæŽ¥ä½äººã€‚

`full-visible-v5-longform` çš„æ„æ€æ˜¯ï¼šv5.0 è¿žç»­è”è¯»åŒ…ã€æºç»“æž„ä¿çœŸã€æ¦‚å¿µé£Žé™©å’Œåå‘æ¡ä»¶è¦åœ¨åº•ç¨¿ä¸­å¯è§ï¼›ä½†è¿™äº›åŽå°æ£€æŸ¥ä¸èƒ½åžæŽ‰æ­£æ–‡ã€‚æ­£æ–‡ä»å¿…é¡»å†™æˆå®Œæ•´æ–‡ç« ï¼Œæœ‰æ ‡é¢˜ã€é“ºé™ˆã€æ¦‚å¿µä¸Šå‡ã€çŽ°å®žå›žè½ã€è¾¹ç•Œå’Œä½™å‘³ã€‚

`crossframe-review` æ˜¯è´¨é‡é—¸ï¼Œä¸æ˜¯é»˜è®¤æˆæ–‡é“¾è·¯çš„æœ€ç»ˆå†™ä½œè€…ã€‚åªè¦æ–‡ç« å±‚æœªå…³é—­ï¼Œæœ€ç»ˆå¯è§äº¤ä»˜å¿…é¡»ä»ç„¶åŒ…å« `# ç»“æž„æ´žå¯Ÿåº•ç¨¿` å’Œ `# æ–‡ç« æ­£æ–‡`ï¼›è´¨é‡é—¸é€šè¿‡æ—¶åªè¿½åŠ æžçŸ­ç»“è®ºæˆ–å†…éƒ¨é€šè¿‡ï¼Œä¸å¾—åªè¾“å‡ºè¯„å®¡æŠ¥å‘Šã€‚åªæœ‰ç”¨æˆ·æ˜Žç¡®è¦æ±‚â€œåªè¦è¯„å®¡/å®Œæ•´è¯„å®¡æŠ¥å‘Š/ä¸è¦æ–‡ç« â€ï¼Œæˆ–è´¨é‡é—¸å‘çŽ°ç¡¬å¤±è´¥ä¸”å¿…é¡»é˜»æ–­å‘å¸ƒæ—¶ï¼Œæ‰å…è®¸æŠŠè¯„å®¡æŠ¥å‘Šä½œä¸ºä¸»è¾“å‡ºã€‚

åªæœ‰åœ¨ç”¨æˆ·æ˜Žç¡®è¯´â€œåªè¦/ä¸è¦æ–‡ç« /ä¸è¦æˆæ–‡/çŸ­ç­”/ä¸‰å¥è¯/è¡¨æ ¼/æ¸…å•/åŽŸå§‹è¯„å®¡/åŽŸå§‹æ¡ˆä¾‹åº“/åŽŸå§‹å¤‡å¿˜å½•/çº¯è¯Šæ–­/ä»…è¡ŒåŠ¨æ–¹æ¡ˆâ€æ—¶ï¼Œæ‰å…³é—­é»˜è®¤æ–‡ç« å±‚ã€‚æ­¤æ—¶åº”ä¿ç•™ç”¨æˆ·æŒ‡å®šçš„äº¤ä»˜ç‰©ã€‚

## ä½•æ—¶ä½¿ç”¨

å½“ä»»åŠ¡ä¸æ˜¯å•ä¸€è¯Šæ–­ï¼Œè€Œå¯èƒ½éœ€è¦å¤šä¸ª CrossFrame skill è¿žç»­åä½œæ—¶ï¼Œä¼˜å…ˆä½¿ç”¨æœ¬ skillï¼š

- ç”¨æˆ·å¸Œæœ›ä½¿ç”¨ CrossFrameï¼Œä½†æ²¡æœ‰æŒ‡å®šå…·ä½“å­ skillã€‚
- ç”¨æˆ·åªè¯´â€œåˆ†æžä¸€ä¸‹/æ€Žä¹ˆçœ‹/è®²è®²/å†™ä¸€ä¸‹â€ï¼Œä¸”æ›´åƒæƒ³çœ‹ä¸€æ®µå¯è¯»è¾“å‡ºã€‚
- å†™æ–‡ç« ã€è¯„è®ºã€æ€æƒ³æ–‡ç« ã€å…¬å…±è¯„è®ºã€ç»„ç»‡å¤ç›˜æ–‡ç« ã€‚
- ç­”è¯»è€…é—®ã€ç¼–è¾‘å›žä¿¡ã€å’¨è¯¢å¼å›žåº”ï¼Œä½†é—®é¢˜èƒŒåŽæœ‰ç»“æž„è¯Šæ–­ã€‚
- æŠŠææ–™æ•´ç†æˆæ¡ˆä¾‹ï¼Œå†å†™åˆ†æžæˆ–æ²‰æ·€æ¦‚å¿µã€‚
- è¯»ä¹¦ã€ç†è®ºã€æ–‡ç« ç ”ç©¶ç¬”è®°ï¼Œéœ€è¦æ¯”è¾ƒä¸Ž CrossFrame çš„å…³è”å’Œä¸åŒã€‚
- å‘½é¢˜è¾©è®ºåŽéœ€è¦æˆæ–‡ã€ç»™ç»“è®ºæˆ–å†™åé©³ã€‚
- å…ˆç”Ÿæˆè¾“å‡ºï¼Œå†è¯„å®¡å®ƒæ˜¯å¦çœŸçš„æŽ¨ç†ã€‚
- ç”¨æˆ·è¯´â€œè¿™äº› skill åº”è¯¥ä¸€èµ·ç”¨â€â€œè¿žç»­è§¦å‘â€â€œæ€»è§„åˆ™â€â€œæ€»å…¥å£â€â€œæ€Žä¹ˆç»„åˆè°ƒç”¨â€ã€‚

è‹¥ä»»åŠ¡éžå¸¸å•ä¸€ï¼Œç›´æŽ¥ä½¿ç”¨å¯¹åº”ä¸“é¡¹ skillï¼Œä¸è¦ç»•è¡Œï¼š

- åªè¦ç»“æž„è¯Šæ–­ï¼š`../crossframe/SKILL.md`
- åªè¦æ–‡ç« ï¼š`../crossframe-essay/SKILL.md`
- åªè¦è¯„å®¡ï¼š`../crossframe-review/SKILL.md`
- åªè¦çŸ­ç­”å¤ï¼š`../crossframe-dialogue/SKILL.md`
- åªè¦æ¡ˆä¾‹åº“ï¼š`../crossframe-casebook/SKILL.md`
- åªè¦å…¬å…±è®®é¢˜è¯æ®è¾¹ç•Œï¼š`../crossframe-public/SKILL.md`
- åªè¦ç»„ç»‡ä¿®å¤å¤‡å¿˜å½•ï¼š`../crossframe-org/SKILL.md`
- åªè¦æ¦‚å¿µæ•™å­¦ï¼š`../crossframe-teach/SKILL.md`
- åªè¦å‘½é¢˜è®ºè¯ï¼š`../crossframe-debate/SKILL.md`
- åªè¦è¯»ä¹¦ç ”ç©¶ç¬”è®°ï¼š`../crossframe-notebook/SKILL.md`

## å¿…é¡»è¯»å–

æ¯æ¬¡è§¦å‘åŽè¯»å–ï¼š

1. `references/output-mode-selector.md`
2. `references/workflow-routing-map.md`
3. `protocols/suite-dispatch-protocol.md`
4. `templates/suite-reasoning-outline.md`

ç„¶åŽæŒ‰è·¯ç”±è¯»å–å¯¹åº” sibling skillã€‚åŸºç¡€ç»“æž„åˆ¤æ–­é€šå¸¸å…ˆè¯» `../crossframe/SKILL.md` ä¸Ž `../crossframe/references/read-routing-map.md`ã€‚

## è°ƒåº¦åŽŸåˆ™

- åŸºç¡€å…ˆè¡Œï¼šå¤šæ•°å¤æ‚ä»»åŠ¡å…ˆç”± `crossframe` å»ºç«‹äº‹å®žè¾¹ç•Œã€å°ºåº¦çª—å£ã€æœºåˆ¶å€™é€‰å’Œåˆ¤æ–­æ¡£ä½ã€‚
- åœºæ™¯è¿½åŠ ï¼šåªè¯»å–æœ¬æ¬¡å¿…è¦çš„ä¸“é¡¹ skillï¼Œä¸æŠŠå…¨éƒ¨ skill ä¸€èµ·è§¦å‘ã€‚
- æˆæ–‡åŽç½®ï¼šå†™æ–‡ç« å‰å…ˆæœ‰ç»“æž„æ´žå¯Ÿåº•ç¨¿ï¼›å…¬å…±ã€ç»„ç»‡ã€è¾©è®ºã€è¯»ä¹¦ç­‰ä¸“é¡¹åˆ¤æ–­å…ˆå®Œæˆï¼Œå†è¿›å…¥ `crossframe-essay`ã€‚
- é»˜è®¤æˆæ–‡ï¼šsuite è¢«è§¦å‘æ—¶ï¼Œæœ€ç»ˆè¾“å‡ºé»˜è®¤èµ° `crossframe-essay`ï¼Œè¾“å‡ºæ¡£ä½å›ºå®šä¸º `full-visible-v5-longform`ï¼›ä¸“é¡¹äº§ç‰©å…ˆåšï¼Œæ–‡ç« åŽç½®ã€‚
- æ¨¡å¼/è§’è‰²å…ˆè¡Œï¼šsuite å¼€å¤´åªç¡®è®¤è¾“å‡ºæ¨¡å¼ä¸Žè§’è‰²ï¼›æ²¡æœ‰è§¦å‘è¯æ—¶å±•ç¤º `templates/mode-selection-dialog.md` å¹¶ç­‰å¾…å›žå¤ï¼Œä¸ç›´æŽ¥å¼€å§‹ã€‚
- æ–‡ç« ç±»åž‹åŽç½®ï¼šæ–‡ç« ç±»åž‹åªåœ¨è¿›å…¥ `crossframe-essay` åŽã€ç»“æž„æ´žå¯Ÿåº•ç¨¿ç”ŸæˆåŽç¡®è®¤ï¼›å®ƒå†³å®šæ–‡ç« è¡¨è¾¾å½¢æ€å’Œå†™ä½œæŠ€æ³•è¯»å–ï¼Œä¸æ”¹å˜ suite çš„ä¸»è·¯ç”±ã€‚
- èƒ¶å›Šå½’å±žï¼šsuite åªä¼ å…¥ `selection_state`ã€`workflow_state`ã€`voice_mode` å’Œæ–‡ç« å±‚å¼€å…³ï¼›ä¸å¾—è¯»å– v5 æºç´¢å¼•ã€ä¸å¾—å±•å¼€è¿žè¯»åŒ…ã€ä¸å¾—ç”Ÿæˆ `v5-read-state-capsule`ã€‚èƒ¶å›Šç”± `crossframe` æ ¸å¿ƒå±‚åœ¨å‘½ä¸­ source modulesã€å…¥å£åŒ…å’Œå¿…é¡»åŒè¯»é—­åŒ…åŽç”Ÿæˆã€‚
- å£°å£ç”±è§’è‰²å†³å®šï¼šsuite é»˜è®¤æˆæ–‡æ—¶ï¼Œæ ¹æ® `output-mode-selector.md` å°† `voice_mode` å’Œ `topic_sensitivity` ä¼ ç»™ `crossframe-essay`ã€‚ç”¨æˆ·æ˜¾å¼è¦æ±‚â€œäº²åˆ‡/ç¼–è¾‘å£å»/ç­”å¤ä½“â€æ—¶è¦†ç›–ã€‚
- é•¿æ–‡å¥‘çº¦ï¼šä»»ä½•ä»Ž suite è¿›å…¥ã€ä¸”æœªæ˜¾å¼å…³é—­æ–‡ç« å±‚çš„ CrossFrame å†…å®¹ä»»åŠ¡ï¼Œé»˜è®¤ä¸æ˜¯çŸ­ç­”ï¼Œä¸å¾—ç”¨é¡¹ç›®ç¬¦å·è¯Šæ–­ã€æ‘˜è¦å¼å›žç­”æˆ–â€œå¦‚æžœåªè¦ä¸€å¥è¯â€æ›¿ä»£å®Œæ•´æ­£æ–‡ã€‚
- æˆæ–‡è¾¹ç•Œï¼šé»˜è®¤å¯¹æ‰€æœ‰ CrossFrame å†…å®¹ä»»åŠ¡æˆæ–‡ï¼›åªæœ‰ç”¨æˆ·ç”¨â€œåªè¦/ä¸è¦æ–‡ç« /çŸ­ç­”/è¡¨æ ¼/æ¸…å•/çº¯è¯Šæ–­/ä»…è¡ŒåŠ¨æ–¹æ¡ˆâ€ç­‰è¯æ˜Žç¡®å…³é—­æ—¶ï¼Œæ‰å…³é—­æ–‡ç« å±‚ã€‚
- æºè¿žç»­æ€§ï¼šé«˜è´£ä»»ã€å…¬å…±åˆ¶åº¦ã€äº²å¯†å…³ç³»ã€é•¿æœŸæ¼”åŒ–ã€æ·±åº¦åˆ†æžã€æ¡†æž¶æ²»ç†ã€AI çŽ°å®žéªŒè¯ã€å¼±ä¿¡å·/ä¸é€æ˜Žã€æ— æ³•é€€å‡ºå’Œæ–‡ç« è¾“å‡ºï¼Œè¦åœ¨è°ƒåº¦ä¸­åˆ—å‡ºæœ¬æ¬¡è§¦å‘çš„ v5.0 è¿žç»­è”è¯»åŒ…ï¼›ä¸è¦åªåˆ—æ¦‚å¿µå¡ã€‚
- æºé”šç‚¹å®Œæ•´æ€§ï¼šå‡¡è¿›å…¥æ–‡ç« å±‚ã€é«˜è´£ä»»ã€å…¬å…±åˆ¶åº¦ã€AI/è¿‡ç¨‹æ€§äº§ç‰©ã€ç”Ÿå‘½å‘¨æœŸã€æ— æ³•é€€å‡ºä¸»ä½“æˆ–æ¡†æž¶æ²»ç†æ—¶ï¼Œè°ƒåº¦æçº²è¦è¦æ±‚ä¸‹æ¸¸å¤ç”¨ `v5-read-state-capsule` å¹¶æ‰§è¡Œæºé”šç‚¹å®Œæ•´æ€§æ£€æŸ¥ã€‚
- è¯„å®¡æ”¶æŸï¼šé‡è¦è¾“å‡ºé»˜è®¤æœ€åŽç”¨ `crossframe-review` åšè´¨é‡é—¸ï¼›è´¨é‡é—¸ä¸å¾—æŽ¥ç®¡æœ€ç»ˆè¾“å‡ºæˆ–åžæŽ‰åº•ç¨¿/æ­£æ–‡ã€‚è½»é‡çŸ­ç­”å¤å¯åªåšå†…éƒ¨è‡ªæ£€ã€‚
- æŸ¥æºå…‹åˆ¶ï¼šå…¬å…±è®®é¢˜ã€çœŸå®žæœºæž„ã€å¹³å°ã€æ”¿ç­–ã€äººç‰©ã€å…¬å¸å’Œæœ€æ–°äº‹å®žè¦æŸ¥æºï¼›ç§äººå…³ç³»ã€å“²å­¦æ³›è®ºã€ç”¨æˆ·è‡ªç»™ææ–™é»˜è®¤ä¸æŸ¥æºã€‚
- äººè¯ä¼˜å…ˆï¼šæœ€ç»ˆè¾“å‡ºå…ˆç»™æ™®é€šäººèƒ½è¯»æ‡‚çš„ç»“æžœï¼Œæœ¯è¯­åªåšå¿…è¦æ˜ å°„ã€‚

## é»˜è®¤è¿žç»­é“¾è·¯

```text
ç»“æž„è¯Šæ–­ï¼š
crossframe -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

å¼€æ”¾å¼å¯è¯»åˆ†æžï¼š
crossframe -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

æ™®é€šæ´žå¯Ÿæ–‡ç« ï¼š
crossframe -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

å…¬å…±è¯„è®ºæ–‡ç« ï¼š
crossframe -> crossframe-public -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

ç»„ç»‡å¤ç›˜/ä¿®å¤æ–‡ç« ï¼š
crossframe -> crossframe-org -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

ç­”è¯»è€…é—®/ç¼–è¾‘å›žä¿¡ï¼š
crossframe -> crossframe-dialogue -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

æ¡ˆä¾‹æ²‰æ·€ï¼š
crossframe -> crossframe-casebook -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

æ¦‚å¿µæ•™å­¦ï¼š
crossframe -> crossframe-teach -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

å‘½é¢˜è¾©è®ºï¼š
crossframe -> crossframe-debate -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

è¾©è®ºåŽæˆæ–‡ï¼š
crossframe -> crossframe-debate -> crossframe-essay -> crossframe-review

è¯»ä¹¦/ç†è®ºç ”ç©¶ï¼š
crossframe -> crossframe-notebook -> crossframe-essay(full-visible-v5-longform) -> crossframe-review

è¯»ä¹¦åŽæˆæ–‡ï¼š
crossframe -> crossframe-notebook -> crossframe-essay -> crossframe-review
```

è¿›å…¥ `crossframe-essay` åŽå…ˆç”Ÿæˆç»“æž„æ´žå¯Ÿåº•ç¨¿ï¼Œå†æ‰§è¡Œæ–‡ç« ç±»åž‹é€‰æ‹©è§„åˆ™ï¼šç”¨æˆ·å·²æ˜¾å¼æŒ‡å®šæ–‡ç« ç±»åž‹æ—¶åœ¨åº•ç¨¿ä¸­è®°å½•å¹¶ç›´æŽ¥é‡‡ç”¨ï¼›ç”¨æˆ·æœªæŒ‡å®šä¸”æ–‡ç« å±‚å¼€å¯æ—¶ï¼ŒåŸºäºŽåº•ç¨¿å±•ç¤º `../crossframe-essay/templates/article-type-selection-dialog.md`ï¼›ç”¨æˆ·å›žå¤â€œé»˜è®¤/è‡ªåŠ¨/éƒ½è¡Œâ€æ—¶é‡‡ç”¨åº•ç¨¿æŽ¨èé¡¹ï¼›ç”¨æˆ·æ˜Žç¡®å…³é—­æ–‡ç« å±‚æ—¶ä¸å±•ç¤ºã€‚

`crossframe-review-lite` è¡¨ç¤ºä¸å¿…è¾“å‡ºå®Œæ•´è¯„å®¡æŠ¥å‘Šï¼Œä½†å¿…é¡»æ£€æŸ¥ï¼šæ˜¯å¦è·³è¿‡äº‹å®žè¾¹ç•Œã€æ˜¯å¦äººæ ¼å®¡åˆ¤ã€æ˜¯å¦æ¦‚å¿µå †ç Œã€æ˜¯å¦è¶Šè¿‡è¯æ®æ¡£ä½ã€‚

## è¾“å‡ºæ–¹å¼

é™¤éžç”¨æˆ·åªé—®â€œè¯¥ç”¨å“ªä¸ª skillâ€ï¼Œå¦åˆ™æœ€ç»ˆè¾“å‡ºå…ˆç»™ä¸€ä¸ªçŸ­è°ƒåº¦æçº²ï¼š

```text
è°ƒåº¦æçº²
- ä»»åŠ¡ç±»åž‹ï¼š
- è¾“å‡ºæ¨¡å¼ä¸Žè§’è‰²ï¼š
- å·¥ä½œæµï¼š
- å¿…è¯» skillï¼š
- æŒ‰éœ€è¯»å–ï¼š
- è¿žç»­è”è¯»åŒ…ï¼š
- ä¸»é¢˜æ•æ„Ÿåº¦ï¼š
- æ­£æ–‡å£°å£ï¼š
- æ–‡ç« ç±»åž‹ï¼š
- è¾“å‡ºæ¡£ä½ï¼š
- ä¸è¯»å–ï¼š
- è´¨é‡é—¸ï¼š
```

ç„¶åŽè¿›å…¥å¯¹åº” skill çš„æ­£å¸¸è¾“å‡ºã€‚ä¸è¦æŠŠè°ƒåº¦æçº²å†™å¾—æ¯”ä»»åŠ¡æœ¬èº«è¿˜é•¿ã€‚

## ç¦æ­¢

- ç¦æ­¢ä¸ºäº†æ˜¾å¾—å®Œæ•´è€Œè§¦å‘å…¨éƒ¨ skillã€‚
- ç¦æ­¢è·³è¿‡ `crossframe` çš„äº‹å®žè¾¹ç•Œå’Œåˆ¤æ–­æ¡£ä½ç›´æŽ¥å†™æ–‡ç« ã€‚
- ç¦æ­¢å…¬å…±è®®é¢˜ä¸æŸ¥æºå´åšå¼ºåˆ¤æ–­ã€‚
- ç¦æ­¢æŠŠ `crossframe-review` å½“ä½œå½¢å¼æ”¶å°¾ï¼›å®ƒå¿…é¡»èƒ½å¦å†³åè¾“å‡ºã€‚
- ç¦æ­¢åœ¨ suite é»˜è®¤æˆæ–‡é“¾è·¯ä¸­åªè¾“å‡ºè´¨é‡é—¸ã€è¯„å®¡ç»“è®ºæˆ–ä¿®å¤å»ºè®®ï¼Œè€Œéšè— `ç»“æž„æ´žå¯Ÿåº•ç¨¿` å’Œ `æ–‡ç« æ­£æ–‡`ã€‚
- ç¦æ­¢è®©è°ƒåº¦è§„åˆ™å–ä»£ä¸“é¡¹ skill çš„åè®®ã€‚

