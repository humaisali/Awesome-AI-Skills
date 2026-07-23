---
name: crossframe-teach
description: "Use when CrossFrame Suite routes explicit Chinese teaching of CrossFrame concepts, misreading boundaries, plain-language examples, signals, or exercises."
category: content
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
  - teaching
  - concepts
  - plain-language
---
# CrossFrame Teach



## When to Use This Skill

- Use when `crossframe-suite` routes explicit CrossFrame work into concept teaching, misreading correction, plain-language examples, observable signals, or exercises.
- Use when the user wants to understand a CrossFrame concept without turning terms into slogans.
- Do not use independently unless the user explicitly names this sibling skill.

## Packaged Source Note

This AAS-ready copy preserves the original CrossFrame skill body below. Chinese remains the canonical semantic layer; English metadata is only for discovery, installation, and repository review.

## Limitations

- The skill body is intentionally Chinese-canonical; English metadata is for discovery and does not replace the original Chinese terms.
- Use only after explicit CrossFrame invocation or `crossframe-suite` routing; do not apply it as a generic default reasoning layer.
- It structures analysis, drafting, and review, but does not replace source verification, domain expertise, or legal, medical, or financial judgment.

> **æœ¬ skill ä¸ç‹¬ç«‹è§¦å‘ã€‚** æ‰€æœ‰ CrossFrame ä»»åŠ¡ç»Ÿä¸€ä»Ž `crossframe-suite` å…¥å£è°ƒåº¦ã€‚ç”¨æˆ·æ— éœ€ç›´æŽ¥è°ƒç”¨æœ¬ skillï¼›suite æ ¹æ®è·¯ç”±è§„åˆ™åœ¨éœ€è¦æ—¶è‡ªåŠ¨åŠ è½½ã€‚

å¦‚æžœæ¦‚å¿µæ•™å­¦è¦è¿žæŽ¥æ–‡ç« å†™ä½œã€æ¡ˆä¾‹æ²‰æ·€ã€è¯»ä¹¦ç ”ç©¶æˆ–è¾“å‡ºè¯„å®¡ï¼Œå…ˆè¯»å– `../crossframe-suite/SKILL.md` åšæ€»è°ƒåº¦ï¼›æœ¬ skill åªè´Ÿè´£æ•™å­¦è§£é‡Šã€è¯¯è¯»è¾¹ç•Œå’Œç»ƒä¹ ã€‚

## è½»å…¥å£åŽŸåˆ™

ä¸­æ–‡æ˜¯æƒå¨è¯­ä¹‰ã€‚`CrossFrame Teach` åªæ˜¯æ•™å­¦å…¥å£ï¼Œä¸é‡å†™ã€ä¸æ›¿ä»£ã€ä¸åŽ‹ç¼© canonical CrossFrameã€‚

æ¯æ¬¡è§¦å‘åŽå…ˆè¯»å–ç›¸é‚» canonical ææ–™ï¼š

- `../crossframe/SKILL.md`
- `../crossframe/references/read-routing-map.md`
- è‹¥æ¦‚å¿µæ•™å­¦è§¦å‘é«˜è´£ä»»ã€å…¬å…±åˆ¶åº¦ã€äº²å¯†å…³ç³»ã€é•¿æœŸæ¼”åŒ–ã€æ¡†æž¶æ²»ç†ã€AI çŽ°å®žéªŒè¯ã€å¼±ä¿¡å·/ä¸é€æ˜Žã€æ— æ³•é€€å‡ºã€å·¥å…·åŒ–ã€éšå–»/æ¥æºé€æ˜Žæˆ–æ–‡ç« è¾“å‡ºï¼Œè¿½åŠ è¯»å– `../crossframe/references/continuity-bundles.md`ï¼Œå¹¶æŒ‰éœ€ä½¿ç”¨ `../crossframe/worksheets/source-continuity-check.md`ï¼›æœªå®Œæˆè”è¯»æ—¶åªèƒ½é™æ¡£ã€‚
- å¤ç”¨ `../crossframe/templates/read-state-capsule.md` è§„å®šçš„ `v5-read-state-capsule`ï¼Œå¹¶åœ¨é«˜è´£ä»»ã€å…¬å…±ã€AI/è¿‡ç¨‹æ€§äº§ç‰©ã€ç”Ÿå‘½å‘¨æœŸã€æ— æ³•é€€å‡ºä¸»ä½“æˆ–æ–‡ç« è¾“å‡ºåœºæ™¯æ‰§è¡Œ `../crossframe/worksheets/source-anchor-integrity-check.md`ã€‚å¦‚æžœèƒ¶å›Šç¼ºå¤±ï¼Œå›žåˆ° `../crossframe/SKILL.md` è¡¥é½ï¼›æœ¬ skill ä¸é‡æ–°å‘æ˜Žæºè·¯ç”±ã€‚

ä¸è¦æŠŠ canonical å…¨æ–‡å¤åˆ¶è¿›å›žç­”ã€‚åªæŒ‰æœ¬æ¬¡æ¦‚å¿µéœ€è¦è¯»å– canonical çš„åè®®ã€æœ¯è¯­ä¿çœŸææ–™ã€æ¦‚å¿µå¡æˆ–æ¨¡æ¿ï¼›æ•™å­¦è¡¨è¾¾ä½¿ç”¨æœ¬ skill çš„è½»é‡åè®®å’Œæ¨¡æ¿ã€‚

## å¿…è¯»èµ„æº

1. è¯»å– `protocols/teach-protocol.md`ï¼Œç¡®å®šæœ¬æ¬¡æ˜¯æ¦‚å¿µè¯¾ã€è¯¯è¯»çº åã€çŽ°å®žä¿¡å·è®­ç»ƒï¼Œè¿˜æ˜¯ç»ƒä¹ é¢˜ç”Ÿæˆã€‚
2. è¯»å– `references/teaching-fidelity.md`ï¼Œé˜²æ­¢æœ¯è¯­å †ç Œã€è§£é‡Šè¿‡çŸ­å¤±çœŸã€é“å¾·åŒ–å’Œæ¼ç»ƒä¹ ã€‚
3. éœ€è¦æˆç¨¿æ—¶ä½¿ç”¨ `templates/concept-lesson.md`ï¼›åªç”Ÿæˆç»ƒä¹ æ—¶ä½¿ç”¨ `templates/micro-exercises.md`ã€‚
4. éœ€è¦å¯¹ç…§æ ·ä¾‹æ—¶è¯»å– `examples/` ä¸­å¯¹åº”æ¦‚å¿µï¼›éœ€è¦è‡ªæµ‹æ—¶è¯»å– `evals/smoke-tests.md`ã€‚

## è¾“å‡ºé¡ºåº

é»˜è®¤æŒ‰è¿™ä¸ªé¡ºåºè¾“å‡ºï¼Œä¸è¦æŠŠæœ¯è¯­æ”¾åœ¨ç¬¬ä¸€æ®µå½“ç»“è®ºï¼š

1. **å…ˆè¯´äººè¯**ï¼šç”¨æ™®é€šç”Ÿæ´»è¯­è¨€è§£é‡Šæ¦‚å¿µåœ¨è¯´ä»€ä¹ˆã€‚
2. **æ¦‚å¿µæ˜ å°„**ï¼šæŠŠäººè¯å¯¹åº”åˆ° 1-3 ä¸ª CrossFrame ç»“æž„é—®é¢˜ã€‚
3. **åä¾‹ä¸Žè¯¯è¯»è¾¹ç•Œ**ï¼šå†™æ¸…ä¸èƒ½è¯¯è¯»æˆä»€ä¹ˆï¼Œç»™ä¸€ä¸ªåä¾‹æˆ–åä¾‹ã€‚
4. **çŽ°å®žè§‚å¯Ÿ**ï¼šåˆ—å‡ºçŽ°å®žé‡Œèƒ½çœ‹è§çš„è¡Œä¸ºã€èµ„æºã€è¾¹ç•Œã€åé¦ˆæˆ–è´£ä»»å˜åŒ–ã€‚
5. **ç»ƒä¹ **ï¼šç»™ 1-3 ä¸ªå°ç»ƒä¹ ï¼Œå¸®åŠ©ç”¨æˆ·è‡ªå·±è¾¨è®¤æ¦‚å¿µè¾¹ç•Œã€‚

å¦‚æžœç”¨æˆ·è¦æ±‚æžç®€ï¼Œä¹Ÿè‡³å°‘ä¿ç•™ä¸€ä¸ªæžçŸ­è‡ªæµ‹é—®é¢˜ï¼Œé™¤éžç”¨æˆ·æ˜Žç¡®è¯´ä¸è¦ç»ƒä¹ ã€‚

## æ•™å­¦è¾¹ç•Œ

- æ¦‚å¿µè§£é‡Šä¸æ˜¯çŽ°å®žè¯Šæ–­ï¼›æ²¡æœ‰äº‹å®žæ—¶ï¼Œä¸ç»™å¼ºåˆ¤æ–­ã€‚
- ä¸æŠŠ CrossFrame æ¦‚å¿µå½“ä½œé“å¾·è¦æ±‚ã€äººæ ¼æ ‡ç­¾ã€å‘½è¿é¢„è¨€æˆ–ä¸“ä¸šæ›¿ä»£å“ã€‚
- ä¸è¯´â€œè¿™æ˜¯å…¸åž‹çš„ Xï¼Œæ‰€ä»¥ Yâ€ï¼›å…ˆè¯´äº‹å®žæ¨¡å¼ï¼Œå†ç»™æ¦‚å¿µæ˜ å°„ã€‚
- ä¸æŠŠâ€œçˆ±/å¼€æ”¾è¡ŒåŠ¨â€è®²æˆç»§ç»­å¿è€ã€ç»§ç»­ç‰ºç‰²æˆ–å–æ¶ˆè´£ä»»é“¾ã€‚
- ä¸æŠŠâ€œå¼€æ”¾æ–­è¨€â€è®²æˆå«ç³Šã€ä¸è´Ÿè´£æˆ–æœ€ç»ˆå®¡åˆ¤ã€‚
- ä¸æŠŠâ€œæ‰¿æŽ¥/å›žæµâ€è®²æˆè„¾æ°”å¥½ã€ä¼šæ²Ÿé€šã€æ€åº¦å˜å¥½æˆ–å•æ–¹è´Ÿè´£ã€‚

## æœ€ä½Žåˆæ ¼æ ‡å‡†

ä¸€æ¬¡åˆæ ¼çš„æ•™å­¦å›žç­”å¿…é¡»èƒ½å›žç­”ï¼š

- æ™®é€šäººç¬¬ä¸€æ®µèƒ½ä¸èƒ½å¬æ‡‚ï¼Ÿ
- è¿™ä¸ªæ¦‚å¿µå¯¹åº”å“ªäº›çŽ°å®žè¡Œä¸ºæˆ–ç»“æž„å˜åŒ–ï¼Ÿ
- å®ƒæœ€å®¹æ˜“è¢«è¯¯è¯»æˆä»€ä¹ˆï¼Ÿ
- å“ªä¸ªåä¾‹èƒ½è®©ç”¨æˆ·çŸ¥é“è¾¹ç•Œåœ¨å“ªé‡Œï¼Ÿ
- ç”¨æˆ·å¯ä»¥è§‚å¯Ÿä»€ä¹ˆä¿¡å·ï¼Ÿ
- ç”¨æˆ·å¯ä»¥åšå“ªä¸€ä¸ªç»ƒä¹ æ¥éªŒè¯è‡ªå·±æ˜¯å¦ç†è§£ï¼Ÿ

## èµ„æºç´¢å¼•

- `protocols/teach-protocol.md`ï¼šæ•™å­¦è§£é‡Šæµç¨‹ã€‚
- `references/teaching-fidelity.md`ï¼šæ•™å­¦ä¿çœŸä¸Žåè¯¯ç”¨è§„åˆ™ã€‚
- `templates/concept-lesson.md`ï¼šå®Œæ•´æ¦‚å¿µè¯¾æ¨¡æ¿ã€‚
- `templates/micro-exercises.md`ï¼šç»ƒä¹ é¢˜æ¨¡æ¿ã€‚
- `examples/chengjie-huiliu.md`ï¼šæ‰¿æŽ¥/å›žæµæ•™å­¦æ ·ä¾‹ã€‚
- `examples/open-assertion.md`ï¼šå¼€æ”¾æ–­è¨€æ•™å­¦æ ·ä¾‹ã€‚
- `examples/love-open-action.md`ï¼šçˆ±/å¼€æ”¾è¡ŒåŠ¨æ•™å­¦æ ·ä¾‹ã€‚
- `examples/failure-patterns.md`ï¼šå¤±è´¥æ ·ä¾‹ã€‚
- `evals/smoke-tests.md`ï¼šsmoke testsã€‚

