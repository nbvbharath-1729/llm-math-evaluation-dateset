# Scoring Rubric — LLM Math Response Evaluation Dataset

## Overview

Each AI-generated math response is evaluated across three independent
dimensions: Correctness, Reasoning, and Clarity. Every dimension is
scored on a scale of 0 to 5 by a human expert evaluator. A weighted
formula combines the three scores into a single Final Score on a
0 to 100 scale.

---

## Scoring Dimensions

| Dimension | Scale | Weight | What it measures |
|---|---|---|---|
| Correctness | 0 – 5 | 50% | Accuracy of the final answer and validity of steps |
| Reasoning | 0 – 5 | 30% | Logical quality and completeness of working shown |
| Clarity | 0 – 5 | 20% | Structure, readability, and organization of response |

All three dimensions are scored independently. A response may score
high on Clarity but low on Correctness (clear but wrong), or high on
Correctness but low on Reasoning (correct answer with no working shown).

---

## Correctness Score (0–5)

Measures whether the final answer is mathematically correct and whether
the steps leading to it are valid.

| Score | Label | Description |
|---|---|---|
| 5 | Fully Correct | Final answer exactly right. All steps are valid and lead correctly to the answer. |
| 4 | Correct with Minor Slip | Final answer correct. One minor arithmetic slip exists in the working but the model recovers correctly. |
| 3 | Right Approach, Wrong Answer | Correct method and formula used. Final answer is wrong due to a calculation or arithmetic error at the end. |
| 2 | Partially Correct | Correct formula identified but set up incorrectly, or partially correct approach with wrong answer. |
| 1 | Mostly Wrong | Wrong approach or method used. Answer is incorrect. Occasional coincidental correct sub-step does not raise this score. |
| 0 | Completely Wrong | Wrong approach, wrong answer, no valid mathematical working present. |

### Correctness Scoring Notes

- The Verified Answer column (cross-checked via Wolfram Alpha) is the
  ground truth. Always compare the AI's final answer to the Verified
  Answer, not the Correct Answer, in case of any discrepancy.
- If the model gives two answers (e.g., corrects itself mid-response),
  the last stated final answer is used for scoring.
- A model that refuses to answer or states it cannot solve the problem
  receives a score of 0.
- A model that gives the correct answer but with completely wrong
  working receives a score of 1, not 5. The working matters.

---

## Reasoning Score (0–5)

Measures the logical quality and completeness of the working shown.
Scored independently of whether the final answer is correct.

| Score | Label | Description |
|---|---|---|
| 5 | Airtight Reasoning | Every step clearly shown. Each step follows logically from the previous. No gaps, no leaps of logic. |
| 4 | Mostly Valid | Reasoning mostly valid and complete. One small logical gap or minor unexplained shortcut. |
| 3 | Core Logic Present | The core method is correct but important intermediate steps are skipped. The working is incomplete. |
| 2 | Significant Gaps | Some valid steps present but major portions of the reasoning are missing or logically disconnected. |
| 1 | Mostly Flawed | Steps do not connect logically. Reasoning is largely incorrect or incoherent. |
| 0 | No Reasoning | Final answer stated with no working shown, or working is entirely irrelevant to the problem. |

### Reasoning Scoring Notes

- A response that gives the correct answer with no steps shown receives
  a Reasoning score of 0 regardless of Correctness score.
- A response that shows correct reasoning but makes an arithmetic error
  at the final step still receives a high Reasoning score (4 or 5).
- Shortcut methods (e.g., "85% of 2000" for a 15% discount problem) are
  valid reasoning and do not reduce the Reasoning score, provided the
  shortcut is explained or self-evident.
- If a response is truncated mid-working, the Reasoning score reflects
  only the reasoning that is visible.

---

## Clarity Score (0–5)

Measures how easy the response is to read, follow, and understand.
Scored independently of mathematical correctness.

| Score | Label | Description |
|---|---|---|
| 5 | Crystal Clear | Well structured, clearly labelled steps, easy to follow without any effort. Any reader can understand it immediately. |
| 4 | Clear | Clear and readable with one or two minor presentation issues (e.g., minor formatting inconsistency, slightly ambiguous phrasing). |
| 3 | Understandable | Followable with some effort. Structure is somewhat disorganized, or language is occasionally unclear. |
| 2 | Hard to Follow | Multiple places where the response is confusing. Steps are poorly labelled, disorganized, or difficult to parse. |
| 1 | Very Confusing | Response structure is poor throughout. Very difficult to identify where steps begin and end. |
| 0 | Incomprehensible | Cannot be followed at all. No discernible structure or explanation. |

### Clarity Scoring Notes

**Factors that reduce Clarity score:**
- No step labels or numbering (reader must guess the structure)
- Final answer buried inside dense paragraphs
- Inconsistent use of mathematical notation
- Very long responses where key steps are hard to locate
- Multiple approaches mixed together without separation
- Grammar or phrasing that makes the explanation ambiguous

**Factors that increase Clarity score:**
- Clear step-by-step structure with numbered or labelled steps
- Final answer clearly marked and separated
- Consistent notation throughout
- Bonus explanation or shortcut method added clearly after the main solution

---

## Error Type Classification

After scoring, classify the primary error present in the response.
If the response is fully correct, write "No Error". If multiple error
types are present, select the one that most directly caused the wrong
final answer.

| Error Type | Definition | Example |
|---|---|---|
| No Error | Response is fully correct. Final answer matches Verified Answer. | All steps correct, answer = ₹1,700 ✓ |
| Calculation Error | Correct method and formula, but arithmetic is wrong. | 15% of 2000 computed as 15 × 200 = 300 (correct) but then subtracted from wrong base |
| Conceptual Error | Wrong formula or wrong mathematical concept applied. | Used simple interest formula for a compound interest problem |
| Methodology Error | Completely wrong approach to the problem type. | Divided price by discount percentage instead of computing percentage of price |
| Incomplete Solution | Stopped working before reaching a final answer. | Found the discount amount but did not compute the selling price |
| Sign Error | Positive and negative values confused. | Got −₹300 discount instead of +₹300, giving ₹2,300 instead of ₹1,700 |
| Symbol Error | Correct calculation but wrong mathematics symbols | using x^2 instead of x² |
| Incomplete Answer | incomplete way of expressing final answer | 200 cm² instead of Area of Rectangle if 200 cm² |
| Unit Error | Correct numerical answer but wrong unit stated. | Wrote ₹1700 km or 1700% instead of ₹1700 |
| Multiple Errors | More than one distinct error type contributed to the wrong answer. | Wrong formula AND arithmetic error present |

---

## Final Score Formula

```
Final Score = (Correctness × 0.5 + Reasoning × 0.3 + Clarity × 0.2) × 20
```

This produces a score on a scale of 0 to 100.

### Score Interpretation

| Final Score | Interpretation |
|---|---|
| 90 – 100 | Excellent response. Correct, well-reasoned, and clearly presented. |
| 75 – 89 | Good response. Minor issues in one dimension. |
| 60 – 74 | Acceptable response. Noticeable weaknesses but usable. |
| 40 – 59 | Weak response. Significant errors or gaps in reasoning or clarity. |
| 20 – 39 | Poor response. Major correctness or reasoning failures. |
| 0 – 19 | Very poor response. Incorrect, unclear, and unreasoned. |

### Worked Examples

**Example 1 — Perfect response**

```
Question:  MP = ₹2,000, Discount = 15%. Find Selling Price.
Response:  Step 1: Discount = 15% of 2000 = 300
           Step 2: Selling Price = 2000 - 300 = 1700
           Final Answer: ₹1,700
           Shortcut: 2000 × 0.85 = ₹1,700

Correctness:  5  (correct answer, valid steps)
Reasoning:    5  (every step shown, shortcut also explained)
Clarity:      5  (numbered steps, final answer clearly stated)
Error Type:   No Error
Final Score:  (5×0.5 + 5×0.3 + 5×0.2) × 20 = 5.0 × 20 = 100
```

**Example 2 — Correct answer, poor reasoning**

```
Question:  MP = ₹2,000, Discount = 15%. Find Selling Price.
Response:  The selling price after 15% discount is ₹1,700.

Correctness:  5  (correct answer)
Reasoning:    0  (no working shown at all)
Clarity:      3  (understandable but no structure)
Error Type:   No Error
Final Score:  (5×0.5 + 0×0.3 + 3×0.2) × 20 = 3.1 × 20 = 62
```

**Example 3 — Right method, wrong arithmetic**

```
Question:  MP = ₹2,000, Discount = 15%. Find Selling Price.
Response:  Step 1: Discount = 15% of 2000 = 15 × 200 = 3000
           Step 2: Selling Price = 2000 - 3000 = -₹1,000
           Final Answer: -₹1,000

Correctness:  2  (right formula setup, but 15/100 × 2000 ≠ 3000)
Reasoning:    4  (steps shown and connected, one arithmetic error)
Clarity:      4  (clear structure, well labelled)
Error Type:   Calculation Error
Final Score:  (2×0.5 + 4×0.3 + 4×0.2) × 20 = 3.0 × 20 = 60
```

**Example 4 — Completely wrong approach**

```
Question:  MP = ₹2,000, Discount = 15%. Find Selling Price.
Response:  Selling Price = 2000 + 15 = 2015
           Final Answer: ₹2,015

Correctness:  0  (wrong method, wrong answer)
Reasoning:    1  (a step is shown but it makes no mathematical sense)
Clarity:      3  (at least the structure is readable)
Error Type:   Methodology Error
Final Score:  (0×0.5 + 1×0.3 + 3×0.2) × 20 = 0.9 × 20 = 18
```

---

## Evaluation Guidelines

### Before Scoring Each Response
1. Read the Correct Answer and Verified Answer columns first.
   Fix the ground truth in your mind before reading the AI response.
2. Read the entire AI response once without scoring.
3. Then score each dimension independently in order:
   Correctness → Reasoning → Clarity.

### Consistency Rules
- Score each model's response without looking at other models' responses
  to the same question first. Independent evaluation prevents bias.
- If a question has an Easy difficulty, do not apply stricter standards
  than for Hard questions. The rubric applies uniformly across all
  difficulty levels.
- When in doubt between two adjacent scores (e.g., 3 or 4), write a
  note in the Evaluator Explanation column explaining the edge case.

### Evaluator Explanation Guidelines
Write one specific sentence per row explaining the scores given.
State what was right or wrong and why.

Good explanation: "Correct answer ₹1,700. Both formula method and
shortcut shown clearly. Full marks across all dimensions."

Good explanation: "Used correct percentage formula but computed
15 × 200 = 3000 instead of 3000, giving wrong final answer.
Methodology valid, arithmetic incorrect."

Weak explanation: "Wrong answer." (does not say why)
Weak explanation: "Good response." (does not say what was good)

---

## Dataset Columns Reference

| Column | Type | Description |
|---|---|---|
| Question ID | String | Unique identifier (Q001 – Q050) |
| Model Name | String | GPT-4o, Claude, or Gemini |
| Topic | String | Math topic category |
| Difficulty | String | Easy, Medium, or Hard |
| Question | String | The math problem text |
| Correct Answer | String | Ground truth answer (manually solved) |
| Verified Answer | String | Cross-verified answer (Wolfram Alpha) |
| AI Response | String | Full LLM-generated solution (plain text) |
| Correctness Score | Integer | 0 – 5 |
| Reasoning Score | Integer | 0 – 5 |
| Clarity Score | Integer | 0 – 5 |
| Error Type | String | One of 10 error type categories |
| Final Score | Float | 0 – 100 (weighted formula) |
| Evaluator Explanation | String | One-sentence human justification |

---

## Version

Rubric Version: 1.0
Dataset: LLM Math Response Evaluation Dataset
Evaluator: **N B V BHARATH**
Date: **SEP 2026**
