# LLM Math Response Evaluation Dataset

A manually curated evaluation dataset of 150 AI-generated 
math responses across 3 LLMs, scored by a human expert evaluator.

## Overview
- 50 math problems across 10 topics
- 3 LLMs evaluated: GPT-4o, Claude, Gemini
- 150 total human-annotated evaluations
- Difficulty levels: 15 Easy, 20 Medium, 15 Hard
- Topics: Arithmetic, Algebra, Percentages, Ratio & Proportion,
  Time & Work, Speed & Distance, Geometry, Averages, 
  Number Theory, Statistics

## Scoring Rubric
Each response is scored on three dimensions (0-5 each):
- Correctness Score: Accuracy of the final answer and steps
- Reasoning Score: Logical validity of the working shown
- Clarity Score: Structure and readability of the response
- Final Score: Weighted formula = 
  (Correctness x 0.5 + Reasoning x 0.3 + Clarity x 0.2) x 20
  Gives a score from 0 to 100.

## Error Types
No Error, Calculation Error, Conceptual Error, 
Methodology Error, Incomplete Solution, Sign Error, 
Unit Error, Multiple Errors

## Files
- dataset.csv — main evaluation dataset (150 rows)
- rubric.md — full scoring rubric with examples
- methodology.md — data collection methodology

## Dataset Columns
| Column | Description |
|---|---|
| Question ID | Unique ID per problem (Q001-Q050) |
| Model Name | LLM that generated the response |
| Topic | Math topic category |
| Difficulty | Easy / Medium / Hard |
| Question | The math problem |
| Correct Answer | Ground truth answer |
| Verified Answer | Cross-verified using Wolfram Alpha |
| AI Response | Full LLM-generated solution |
| Correctness Score | 0-5 |
| Reasoning Score | 0-5 |
| Clarity Score | 0-5 |
| Error Type | Classification of error if any |
| Final Score | Weighted score 0-100 |
| Evaluator Explanation | Human justification for scores |

## Author
**N B V BHARATH** — Independent AI Evaluation Researcher
