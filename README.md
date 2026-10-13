# Gemma × bellaOS — Training Lab

**Subtract Architect Studios · Intelligence by Subtraction**

A supervised, evidence-driven training and evaluation workspace for **Gemma 3 270M IT**, with **Bella** acting as lead reasoning agent/trainer, **bellaOS** providing deterministic governance, and **Michael Chaves** retaining final authority.

> **Status:** Training-lab design and operating protocol. This repository does **not** by itself provide an autonomous agent connection, fine-tuned model, or validated performance results.

## Mission

Develop a dependable, low-cost in-house assistant by assigning small, well-scoped tasks to Gemma; evaluating outputs against evidence; documenting mistakes; correcting retrieval or workflows before considering expensive fine-tuning; and escalating risk, ambiguity, or authorization decisions to the owner.

**Primary metric:** total cost per *verified successful task*, not tokens saved in isolation.

## Roles and authority

| Actor | Role | Authority |
| --- | --- | --- |
| Michael Chaves | Owner / final approver | Approves spending, consequential changes, policy revisions, and unresolved conflicts |
| Bella (GPT-based lead agent) | Trainer, evaluator, coordinator | Proposes assignments, selects relevant methods, critiques results, recommends corrections and escalation |
| Gemma 3 270M IT | Supervised apprentice | Executes bounded, approved low-risk assignments; reports uncertainty |
| bellaOS control plane | Deterministic enforcement | Enforces budgets, permissions, approval gates, evidence capture, and rollback |
| CNS / methodology RAG | Versioned knowledge | Supplies minimal relevant approved references and verified prior solutions |

**Important:** ChatGPT does not continuously watch this repository or control a local Gemma process merely because the repository exists. Automated supervision requires an explicitly configured runner/API integration, credentials, and execution permissions. GitHub issues and pull requests can be used for asynchronous check-ins without an always-on agent.

## Operating loop

1. **Negative Step Zero:** Check whether the task is needed, already solved, or doable without inference.
2. **Preflight:** Record purpose, scope, quality floor, allowed tools, data sensitivity, and a default **$0 external spend** budget.
3. **Retrieve:** Select the smallest relevant approved methodology excerpt and prior verified solution; never load the entire RAG by default.
4. **Assign:** Give Gemma a bounded task with acceptance tests and explicit stop conditions.
5. **Evaluate:** Prefer deterministic tests, source evidence, and independent checks over self-reported confidence.
6. **Grade:** Record a ternary evidence verdict: **+1 verified**, **0 unresolved**, **−1 contradicted**. Record separate task-specific metrics rather than turning this verdict into a misleading overall intelligence score.
7. **Correct:** Diagnose whether the failure is due to missing context, retrieval, prompt, tool, routing, or model capability.
8. **Retest:** Run the failed case plus regression cases. Do not claim an improvement without comparison.
9. **Escalate:** Request Michael's approval for consequential actions, spending, unresolved conflicts, or exceptions to policy.
10. **Promote:** Save only reviewed, evidence-backed corrections to the verified knowledge base.

## Suggested repository structure

```text
README.md
governance/
  authority-matrix.md
  approval-policy.md
methodology_rag/
  index.json
  methods/
assignments/
  README.md
evaluations/
  README.md
corrections/
  README.md
regression_tests/
  README.md
reports/
  README.md
templates/
  assignment.md
  evaluation.md
  correction.md
```

These directories are **proposed**, not yet created. Begin with a few Markdown files and GitHub Issues; add tooling only when repeated manual work justifies it.

## Assignment template

Use a GitHub Issue (or `templates/assignment.md`) with:

- **ID / title / owner / date**
- **Purpose and -Step0 result**
- **Inputs and source references** (no secrets or private data)
- **Approved methodology IDs and versions**
- **Expected output and quality threshold**
- **Allowed tools / maximum spend / deadline**
- **Test cases and stop conditions**
- **Gemma output artifact reference**
- **Bella review and evidence verdict**
- **Owner decision** if escalation is required

## Grading and error log

Every evaluated attempt should record:

| Field | Meaning |
| --- | --- |
| Assignment ID | Traceable issue or artifact |
| Model and configuration | Exact model revision, quantization, prompt/template version |
| Methodology IDs | Which retrieved methods were supplied |
| Input/output token counts | Measured with a named tokenizer |
| Runtime/cost | Include retries, verification, and human effort where measurable |
| Expected vs. actual | Reproducible failure description |
| Verdict | −1 contradicted / 0 unresolved / +1 verified |
| Root-cause hypothesis | Clearly distinguish hypothesis from confirmed cause |
| Correction | RAG, workflow, routing, prompt, tool, or training-data change |
| Regression result | Before/after comparison |
| Approval | Who approved promotion or deployment |

**RAG updates are not weight training.** Store validated examples separately for potential future fine-tuning. Do not fine-tune until simpler fixes have been tested.

## Public repository policy

This repository can remain **public for methodology, synthetic assignments, grading rubrics, and sanitized benchmark summaries**. Keep the following out of public commits and issues:

- API keys, credentials, tokens, internal endpoints, or infrastructure secrets
- Customer, employee, tenant, applicant, or other personal data
- Raw private conversations, proprietary prompts, unpublished intellectual property, and unapproved training datasets
- Security incident details that could expose exploitable weaknesses
- Model outputs or claims presented as verified without reproducible evidence

Use a **separate private repository or private storage** for sensitive training inputs, internal evaluations, and commercial IP. Changing a repository to private later does **not** erase copies already cloned or cached.

## Initial milestones

- [ ] M0: Approve authority matrix, publication policy, and benchmark rubric
- [ ] M1: Inspect existing bellaOS/CNS code to avoid duplicate implementations
- [ ] M2: Add 10–20 synthetic, low-risk assignments with reference answers
- [ ] M3: Run Gemma baseline; capture failures and reproducible metrics
- [ ] M4: Add targeted methodology retrieval; rerun the same evaluation set
- [ ] M5: Test escalation to Bella for unresolved cases, with owner approval gates
- [ ] M6: Publish only sanitized, independently verified aggregate results

## Success criteria

The lab succeeds when Gemma handles a growing **measured** share of appropriate low-risk tasks while maintaining the required quality floor, reducing unnecessary paid inference and owner interruptions, and escalating whenever its delegated authority ends.

**Guiding rule:** *Solve once. Verify independently. Reuse responsibly. Escalate deliberately.*
