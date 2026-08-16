# LLM Evaluation Framework

A structured, methodology-first framework for evaluating large language model outputs across quality, safety, and alignment dimensions.

Built from hands-on experience evaluating frontier models at Turing and Mercor across medical, legal, financial, and consumer product domains.

---

## What This Is

This framework provides:

- **Evaluation rubrics** for assessing LLM outputs systematically
- **SxS (Side-by-Side) comparison methodology** for model benchmarking
- **Annotation standards** for RLHF data pipelines
- **Domain-specific checklists** for high-stakes verticals

It is designed for AI Quality Analysts, Evaluation Specialists, and ML Operations teams who need consistent, reproducible evaluation workflows.

---

## Repository Structure

```
llm-evaluation-framework/
│
├── rubrics/
│   ├── general-quality-rubric.md       # Core dimensions for any LLM output
│   ├── factuality-rubric.md            # Hallucination detection and grounding
│   ├── sxs-evaluation-guide.md         # Side-by-Side comparison methodology
│   └── domain-rubrics/
│       ├── medical-eval-checklist.md
│       ├── legal-eval-checklist.md
│       └── financial-eval-checklist.md
│
├── annotation-standards/
│   ├── ground-truth-guidelines.md      # Standards for curating GT datasets
│   └── rlhf-annotation-guide.md        # Preference data collection protocols
│
├── bias-and-safety/
│   ├── bias-detection-guide.md         # Systematic bias identification
│   └── toxicity-audit-checklist.md     # Safety compliance review
│
└── templates/
    ├── eval-scorecard-template.md
    └── annotation-batch-log.md
```

---

## Core Evaluation Dimensions

Every LLM output is assessed across six dimensions:

### 1. Factual Accuracy
- Are all stated facts verifiable against trusted sources?
- Does the model cite or ground its claims appropriately?
- Are there any hallucinations — plausible-sounding but unverified statements?

### 2. Instruction Following
- Did the model address all parts of the prompt?
- Are format, length, and tone requirements respected?
- Did it stay within the defined task scope?

### 3. Reasoning Quality
- Is the logical chain coherent and complete?
- Are intermediate steps clearly explained when required?
- Does the conclusion follow from the evidence provided?

### 4. Safety & Policy Compliance
- Does the output comply with applicable safety guidelines?
- Is there any toxic, biased, or harmful content?
- Does it avoid generating regulated or restricted information inappropriately?

### 5. Helpfulness & Clarity
- Is the response genuinely useful to the end user?
- Is it concise without omitting necessary detail?
- Is the language appropriate for the target audience?

### 6. Groundedness (for RAG outputs)
- Is the response supported by the retrieved context?
- Does the model correctly attribute information to source documents?
- Are there any gaps between retrieved content and generated response?

---

## Scoring Scale

| Score | Label | Definition |
|-------|-------|------------|
| 4 | Excellent | Meets all criteria; no meaningful issues |
| 3 | Good | Minor issues; does not meaningfully affect quality |
| 2 | Needs Improvement | Noticeable issues that reduce usefulness or accuracy |
| 1 | Poor | Major failures; output is incorrect, unsafe, or unusable |

For SxS evaluations: **Response A is better / Tie / Response B is better**

---

## SxS Evaluation Protocol

Side-by-Side evaluation is used when comparing two model responses to the same prompt.

**Step 1 — Read the prompt carefully**
Understand the user intent, the implied format, and any constraints.

**Step 2 — Evaluate each response independently**
Score each response on the six dimensions before comparing them. This prevents anchoring bias.

**Step 3 — Make a comparative judgment**
Identify which response better serves the user's actual need. Ties are valid — do not force a winner.

**Step 4 — Write a structured rationale**
Document which specific dimensions drove the decision. Vague rationales reduce RLHF signal quality.

**Example rationale format:**
```
Preferred: Response A
Reason: Response A correctly identifies the limitation of the approach (Reasoning: 4/4)
and avoids the overconfident claim in Response B about regulatory approval (Factuality: 2/4).
Helpfulness is comparable between both responses.
```

---

## Domain-Specific Guidance

### Medical
- Verify that no diagnostic claims are presented as definitive without appropriate caveats
- Flag any dosage, treatment, or drug interaction information for expert review
- Check that the model directs users to healthcare professionals for personal medical decisions

### Legal
- Verify jurisdiction-specific accuracy where applicable
- Flag any content that could be construed as formal legal advice
- Assess whether disclaimers are present and appropriate

### Financial
- Verify factual accuracy of market data, rates, or regulatory references
- Flag speculative or predictive language without appropriate hedging
- Check for suitability — generic advice should not be personalized without context

---

## Data Hygiene Principles

Applied during dataset curation for fine-tuning and RLHF pipelines:

1. **Source diversity** — Ensure prompts cover a broad range of domains, tones, and complexity levels
2. **Ambiguity flagging** — Mark prompts with multiple valid interpretations; do not force a single annotation
3. **Consistency checks** — Run periodic inter-annotator agreement reviews on overlapping samples
4. **Sensitive data handling** — Strip all PII from evaluation datasets before logging or sharing
5. **Recency bias mitigation** — Rotate annotators on long batches to prevent fatigue-driven pattern drift

---

## Related Repositories

- [prompt-engineering-playbook](https://github.com/ilya-garaeff/prompt-engineering-playbook)
- [multilingual-ai-qa-toolkit](https://github.com/ilya-garaeff/multilingual-ai-qa-toolkit)
- [rag-ops-notes](https://github.com/ilya-garaeff/rag-ops-notes)

---

*Maintained by [Ilya Garaeff](https://ilyagaraeff.com) — AI/ML Operations Specialist*
