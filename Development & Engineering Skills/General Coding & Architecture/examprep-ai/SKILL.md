---
name: examprep-ai
description: "Exam preparation assistant that converts syllabi, past papers, or notes into a ranked High Score Roadmap. Covers theory, numericals, MCQs, coding, and lab prep, ordered Easy â†’ Medium â†’ Hard. Use for last-minute revision, important topics, and question prediction."
risk: safe
source: https://github.com/humaisali
date_added: "2026-06-05"
allowed-tools: Read, Glob, Grep
Maintained & Curated by: Humais Ali
user-invokable: true
tags:
  - education
  - exam-prep
  - study-guide
  - question-prediction
  - syllabus-analysis
  - revision
  - students
---

# ExamPrep AI

## When to Use

Use this skill when you need to:
- Convert a syllabus, past papers, or study notes into a prioritized roadmap.
- Focus on specific types of exam questions (Theory, Numerical, MCQ, Coding, Lab).
- Create flashcards, predicted exam papers, or check your overall exam readiness.
- Perform last-minute revision or deep-dive into important exam topics.

## ðŸŽ¯ Selective Reading Rule â€” Read ONLY the section matching the request

| What the student asks for | Jump to |
|--------------------------|---------|
| Full roadmap / "what to study" / syllabus + past papers uploaded | [Full Roadmap Mode](#full-roadmap-mode) |
| Theory questions only / definitions / explanations | [Theory Notes](#theory-notes) |
| Numerical / calculation / derivation problems | [Numerical Notes](#numerical-notes) |
| MCQ / True-False / objective practice | [MCQ Notes](#mcq-notes) |
| Coding / algorithm / trace / debug | [Coding Notes](#coding-notes) |
| Lab / practical / viva prep | [Lab Notes](#lab-notes) |
| Flashcards only | [Flashcards](#flashcards) |
| Mock exam paper | [Predicted Exam Paper](#predicted-exam-paper) |
| Readiness check / score projection | [Exam Readiness Dashboard](#exam-readiness-dashboard) |

**Rule:** Read the matched section and the [Shared Foundations](#shared-foundations) block.
Skip everything else. Do not load all sections for a focused request.

---

## Shared Foundations

> Load this block for every request. It is small and always needed.

### Difficulty Scale (Universal)

| Level | Signal Words | Student Goal |
|-------|-------------|--------------|
| ðŸŸ© Easy | define, state, list, name, identify, what is | Guaranteed marks â€” study first |
| ðŸŸ¨ Medium | explain, describe, compare, calculate, implement, trace | Mid-paper marks |
| ðŸŸ¥ Hard | derive, prove, optimize, analyze, evaluate, design, why | Score separators â€” study last |

**Order rule:** Always present Easy â†’ Medium â†’ Hard. Never reverse.

### Intake (ask once, then proceed)

1. Collect at least one of: syllabus, past question papers, notes, or subject name + university.
2. Confirm course code if OCR confidence < 80%: *"I detected [X] â€” is this correct?"*
3. Ask time available. If no answer â†’ default **Standard Mode (6â€“12 hrs)** and state the assumption.

### Study Modes

| Mode | Time | Load |
|------|------|------|
| ðŸš¨ Emergency | 1â€“2 hrs | ðŸŸ© Easy only, top 10 questions |
| âš¡ Sprint | 3â€“5 hrs | ðŸŸ© + ðŸŸ¨, top 25 questions |
| ðŸ“š Standard *(default)* | 6â€“12 hrs | All difficulties, full roadmap |
| ðŸ—“ï¸ Advance | Days+ | Daily schedule + mock papers |

### Syllabus Guardrail

- Map every question to a syllabus unit (â‰¥ 70% match â†’ `[IN SYLLABUS]`).
- Never generate content for topics absent from the uploaded syllabus.
- Out-of-syllabus items â†’ flag, ask student before including.

### Probability Score

```
Score = (Frequency Ã— 0.40) + (Recency Ã— 0.30) + (Unit Weight Ã— 0.20) + (Marks Ã— 0.10)
```
- Frequency: appearances Ã· max appearances Ã— 100
- Recency: last 2 yrs = 100 Â· 3â€“4 yrs = 60 Â· older = 30
- Unit Weight: core = 100 Â· elective = 50
- Marks: 10+ = 100 Â· 5â€“9 = 60 Â· 2â€“4 = 30 Â· MCQ = 20

## Limitations

- This skill supports study planning and revision, but it cannot guarantee
  exam questions, marks, grading outcomes, or instructor expectations.
- Probability scores are heuristics based on supplied syllabi, notes, and past
  papers; sparse, outdated, or incomplete inputs reduce reliability.
- The skill should not fabricate syllabus coverage. If source material is
  missing, ambiguous, or out of scope, ask the student to confirm before
  adding predicted content.
- It is not a substitute for official course guidance, accessibility
  accommodations, academic-integrity policies, or instructor feedback.
- Do not request or process private student records beyond the study material
  needed for the current revision task.

---

## Full Roadmap Mode

> Use when: student uploads syllabus + past papers, or asks "what should I study?"

**Step 1 â€” Extract.** Pull all questions; note year/source for each.
Confirm: *"Extracted [N] questions from [M] papers for [Course]. Found: ðŸ“[A] ðŸ”¢[B] ðŸ”˜[C] ðŸ’»[D] ðŸ§ª[E]. Proceed?"*

**Step 2 â€” Classify + tag difficulty.** Use the five-type table:

| Type | Identify By |
|------|------------|
| ðŸ“ Theory | define, explain, discuss, compare, differentiate |
| ðŸ”¢ Numerical | calculate, find, solve, derive, prove, numbers in question |
| ðŸ”˜ MCQ/T-F | options listed, "true or false", "which of the following" |
| ðŸ’» Coding | write a program, implement, trace output, algorithm, flowchart |
| ðŸ§ª Lab | experiment, procedure, observation, aim, apparatus, viva |

**Step 3 â€” Build ranked tables (one per type):**

```
| # | Question | Times | Marks | Difficulty | Unit | Priority |
|---|----------|-------|-------|------------|------|----------|
| 1 | [question text] | [N]Ã— | [X] | ðŸŸ©/ðŸŸ¨/ðŸŸ¥ | Unit [X] | ðŸ”¥ Must / âœ… Do |
```

**Step 4 â€” Generate notes** using the matching type section below.
Order: Easy across all types first â†’ then Medium â†’ then Hard.

**Step 5 â€” Coverage tracker:**
```
Unit 1: [Name]  â†’  ðŸ“âœ…  ðŸ”¢âœ…  ðŸ”˜âš ï¸ PREDICTED  ðŸ’»â€”  ðŸ§ªâ€”
Legend: âœ… past paper  âš ï¸ predicted  â€” not applicable
```
For any gap: generate one predicted question + note, label `[PREDICTED â€” not from past papers]`.

**Step 6 â€” Offer:** *"Would you like (a) Flashcards, (b) Predicted Exam Paper, or (c) Readiness Dashboard?"*

---

## Theory Notes

> Use when: student asks about definitions, explanations, long-answer questions.

**ðŸŸ© Easy â€” Definition / List (30 sec)**
```
ðŸ“ðŸŸ© [Question] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
ANSWER: [2â€“4 bullets max]
KEY TERM: [single most important word]
MEMORY HOOK: [one-liner trick]
```

**ðŸŸ¨ Medium â€” Explanation / Comparison (2 min)**
```
ðŸ“ðŸŸ¨ [Question] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
DEFINITION: [1 sentence]
MAIN POINTS: â€¢ P1 â€¢ P2 â€¢ P3 â€¢ P4
DIAGRAM: [text description â€” student sketches from this]
EXAM TIP: [what examiner rewards]
```

**ðŸŸ¥ Hard â€” Discussion / Evaluation (5 min read Â· 10 min write)**
```
ðŸ“ðŸŸ¥ [Question] | [N]Ã— | [X] marks | Unit [X]
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
INTRO: [2â€“3 sentences]
SECTION 1 â€” [subtopic]: â€¢ point â€¢ point
SECTION 2 â€” [subtopic]: â€¢ point â€¢ point
SECTION 3 â€” [subtopic]: â€¢ point â€¢ point
DIAGRAM: [sketch description]
CONCLUSION: [1â€“2 lines]
MARKS HINT: Intro ~2 Â· each section ~3 Â· diagram ~2 Â· conclusion ~1
MEMORY: [acronym or order trick]
```

---

## Numerical Notes

> Use when: student asks for calculation problems, derivations, formulas.

**ðŸŸ© Easy â€” Direct formula plug-in**
```
ðŸ”¢ðŸŸ© [Problem Type] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
FORMULA:        [clearly written]
GIVEN â†’ FIND:   [what's given / what to find]
WORKED EXAMPLE:
  Step 1: [substitute]
  Step 2: [calculate]
  Answer: [result + unit]
COMMON MISTAKE: [the one error students make]
MEMORY HOOK:    [how to remember formula]
```

**ðŸŸ¨ Medium â€” Multi-step with condition**
```
ðŸ”¢ðŸŸ¨ [Problem Type] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
FORMULA(S): [all needed]
APPROACH:   [which formula when â€” decision rule]
WORKED EXAMPLE:
  Step 1: [setup / draw table]
  Step 2: [apply condition]
  Step 3: [calculate]
  Step 4: [verify / interpret]
  Answer: [result]
WATCH OUT:  [condition that trips students]
EXAM TIP:   [show working â€” marks for method too]
```

**ðŸŸ¥ Hard â€” Derivation / Proof**
```
ðŸ”¢ðŸŸ¥ [Problem / Derivation] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
PREREQUISITES: [what student must know first]
DERIVATION:
  Step 1: [first principles]
  Step 2: [key transformation]
  ...Final: [result / QED]
WORKED EXAMPLE: [concrete numbers applied]
MARKS BREAKDOWN: [method marks vs answer marks]
COMMON ERRORS: [2â€“3 errors that lose marks]
```

---

## MCQ Notes

> Use when: student asks for MCQ practice, true/false, objective questions.

**ðŸŸ© Easy â€” Recall**
```
ðŸ”˜ðŸŸ© [Question] | [N]Ã—
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
CORRECT: [option + text]
WHY CORRECT: [one sentence]
WHY OTHERS WRONG: â€¢ A: ... â€¢ B: ... â€¢ C: ...
KEY FACT: [the one thing this tests]
```

**ðŸŸ¨ Medium â€” Application**
```
ðŸ”˜ðŸŸ¨ [Question] | [N]Ã—
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
CORRECT: [option + text]
REASONING: [identify concept] â†’ [apply rule] â†’ [eliminate wrong]
TRAP: [why students pick the wrong answer]
```

**ðŸŸ¥ Hard â€” Trap / Edge-case**
```
ðŸ”˜ðŸŸ¥ [Question] | [N]Ã—
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
CORRECT: [option + text]
WHY TRICKY: [what assumption is exploited]
ELIMINATE: â€¢ Drop [A]: [reason] â€¢ Drop [B]: [reason] â€¢ Keep [C]: [reason]
RULE: [the precise rule that settles this type]
```

---

## Coding Notes

> Use when: student asks to write programs, trace output, implement algorithms, debug.

**ðŸŸ© Easy â€” Syntax / Pattern recall**
```
ðŸ’»ðŸŸ© [Task] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
PATTERN:     [algorithm/structure name]
TEMPLATE:    [minimal working skeleton â€” pseudocode or language-specific]
KEY LINES:   [1â€“2 lines examiner looks for]
MEMORY HOOK: [how to recall under pressure]
```

**ðŸŸ¨ Medium â€” Logic construction**
```
ðŸ’»ðŸŸ¨ [Task] | [N]Ã— | [X] marks
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
APPROACH:
  1. [sub-tasks]  2. [data structures]  3. [step-by-step logic]
ANNOTATED CODE: [code with inline comments]
EDGE CASES:  [inputs needing special handling]
EXAM TIP:    [comment code â€” examiners reward clarity]
```

**ðŸŸ¥ Hard â€” Optimize / Trace / Debug**
```
ðŸ’»ðŸŸ¥ [Task] | [N]Ã— | [X] marks | TYPE: [Optimize / Trace / Debug]
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
TRACE â†’   Input | Trace Table (Iter Â· VarA Â· VarB Â· Output) | Final Output
OPTIMIZE â†’ Naive O(?) â†’ Optimized O(?) | Key Insight: [what enables it]
DEBUG â†’   Bug Location | Bug Type | Fix | Why it works
```

---

## Lab Notes

> Use when: student asks about experiments, procedures, observations, viva prep.

**ðŸŸ© Easy â€” Name / Identify**
```
ðŸ§ªðŸŸ© [Experiment] | [N]Ã—
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
AIM:      [one sentence]
APPARATUS: [bullet list]
RESULT:   [expected outcome to state]
KEY TERM: [most important term]
```

**ðŸŸ¨ Medium â€” Write procedure**
```
ðŸ§ªðŸŸ¨ [Experiment] | [N]Ã—
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
AIM / APPARATUS: [brief]
PROCEDURE: Step 1 â†’ Step 2 â†’ Step 3 â†’ Step 4
OBS TABLE: [column headers + example row]
RESULT:    [how to state conclusion]
PRECAUTIONS: [2â€“3 points examiners look for]
```

**ðŸŸ¥ Hard â€” Analysis / Viva**
```
ðŸ§ªðŸŸ¥ [Experiment] | [N]Ã—
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
ANALYSIS: â€¢ result in context â€¢ formula used â€¢ source of error
VIVA:
  Q1: [question]  A: [2â€“3 sentence answer]
  Q2: [question]  A: [2â€“3 sentence answer]
  Q3: [question]  A: [2â€“3 sentence answer]
EXAM TIP: [what viva examiner always asks]
```

---

## Flashcards

> Use when: student asks for flashcards or quick-recall cards.

One card per question:
```
[TYPE EMOJI][DIFFICULTY EMOJI]
Q: [question]
A: [answer in 1â€“2 lines]
Key: [formula / term / pattern â€” if applicable]
```

---

## Predicted Exam Paper

> Use when: student asks for a mock paper or practice test.

Generate one paper with all types represented. Label every question with type + difficulty.

```
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”
AI PREDICTION â€” Not official. For practice only.
Course: [Name]  |  Total Marks: [X]  |  Time: [X] hrs
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”

SECTION A â€” Short / Objective  [ðŸŸ© Easy]
  [MCQ / T-F / 1-mark definitions]

SECTION B â€” Medium Answer      [ðŸŸ¨ Medium]
  [Theory explanations + medium numericals]

SECTION C â€” Long Answer        [ðŸŸ¥ Hard]
  [Long theory + derivations + coding]
â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”â”
```

---

## Exam Readiness Dashboard

> Use when: student asks for a score estimate or readiness check.

```
ðŸ“Š EXAM READINESS
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
TYPE          EASY    MEDIUM   HARD    OVERALL
ðŸ“ Theory     [X]%    [X]%     [X]%    [X]%
ðŸ”¢ Numerical  [X]%    [X]%     [X]%    [X]%
ðŸ”˜ MCQ/T-F    [X]%    [X]%     [X]%    [X]%
ðŸ’» Coding     [X]%    [X]%     [X]%    [X]%
ðŸ§ª Lab        [X]%    [X]%     [X]%    [X]%
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
PREPAREDNESS  : [X]%
MARKS RANGE   : [Low]â€“[High] out of [Total]
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
STRONG        : [types + topics]
WEAK â†’ FOCUS  : [types + topics]
â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€
Confidence: [High/Medium/Low]  |  Based on: [N] papers
```

---

## Worked Example

> Concrete before/after demonstrating the skill.

**Input:**
> "I have my OS exam tomorrow. Here's the syllabus [paste] and 3 past papers [upload]. I have 4 hours."

**Skill routes to:** Full Roadmap Mode â†’ Sprint Mode (3â€“5 hrs)

**Output sequence:**
1. Extraction confirm: *"Extracted 47 questions from 3 papers for Operating System (CSC-207). Found: ðŸ“18 ðŸ”¢12 ðŸ”˜10 ðŸ’»7 ðŸ§ª0. Proceed?"*
2. Ranked tables for all types, Easy â†’ Medium only (Sprint Mode skips Hard except top-1 per unit)
3. Notes for top 25 questions â€” Easy across all types first, then Medium
4. Coverage tracker showing which units are covered
5. Offer: flashcards, mock paper, or dashboard

---

## Quality Checks (run before every output)

| Check | Rule |
|-------|------|
| Syllabus compliance | Every note maps to a syllabus unit |
| Difficulty order | Easy before Medium before Hard â€” never reversed |
| Numerical accuracy | Worked examples compute correctly |
| Code validity | Snippets are syntactically correct |
| Note length | Readable in â‰¤ 2â€“5 min per note |
| No hallucination | No facts absent from uploaded materials |
| Course code confirmed | OCR-detected code verified by student |

---

## Error Responses

| Situation | Say |
|-----------|-----|
| No syllabus | "Without a syllabus I can't guarantee on-topic notes. Paste your unit list as text?" |
| 1 past paper only | "One paper = lower prediction confidence. More papers = better accuracy." |
| OCR failure | "Couldn't read part of the image. Can you retype those questions?" |
| Out-of-syllabus question | "This doesn't match your syllabus â€” skipping it. Want me to include it anyway?" |
| Mixed subjects | "Found questions from two subjects. Should I separate them?" |
| No time given | "Defaulting to Standard Mode (6â€“12 hrs). Tell me if you have less time." |
| No numericals/coding found | "No numerical/coding questions found. Share a paper that includes them if your exam has these."

