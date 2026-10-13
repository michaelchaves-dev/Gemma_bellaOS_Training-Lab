# V1 Foundations — Kindergarten through Grade 3

**Status:** Assignment bank only. No Gemma execution or grading has occurred.

## Scope
40 short, objective questions: 10 per grade band K, 1, 2, and 3. Keep V1 binary pass/fail only. **No ternary, RAG instruction, model routing, autonomous code changes, or advanced optimization.**

## How to run
1. Preserve the original Gemma 3 270M IT checkpoint and note its revision, tokenizer, prompt template, inference settings, and runtime.
2. Present **one question per independent request**. Do not include the answer key in the model prompt. Use the same simple instruction for every question: `Answer the question briefly. Give only the answer.`
3. Record the raw response before grading. Grade each against the expected answer; normalize case and whitespace and allow only documented equivalent forms (e.g., `four` for `4`). Do not silently accept semantically different answers.
4. Record pass/fail, failure type, latency, and token counts when available. For arithmetic, compare numeric meaning, not punctuation.
5. Repeat in separate sessions to test consistency, **without training on or revealing the held-out questions between runs**. Mark any reused question as no longer held out after it becomes training material.
6. Bella reviews errors and proposes minimal fixes; Michael approves material changes. No model-weight updates are implied by these exercises.

## Progression
Start with K questions only; do not jump to grade 3 because they are available. Move to the next grade only after repeated, verified success under a pre-agreed threshold. Suggested initial gate: >= 19/20 correct across two distinct K runs, with every failure reviewed. This is a proposed standard, not a result.

## File
`k3_questions.csv` contains ID, grade, prompt, and reference answer. **Do not provide this CSV directly to Gemma**: the answer key must stay on the evaluator side.

## Gemini review
Ask Gemini to review clarity, answer-key correctness, ambiguity, grade progression, evaluation leakage, and whether 270M outputs need additional normalization. Ask for proposed edits, **not automatic commits**. Gemini cannot control a local Gemma process through ordinary chat; integration requires a runner and explicit permissions.

## Security
The repository is public. Use only synthetic educational data here. Never commit API keys, student information, private evaluations, or unpublished proprietary training material.
