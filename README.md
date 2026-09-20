# LLM Math Response Evaluation Dataset

A manually curated evaluation dataset of 150 AI-generated 
math responses across 3 LLMs, scored by a human expert evaluator.

## Overview
- 50 math problems across 10 topics
- 3 LLMs evaluated: GPT-4o, Claude, Gemini
- 150 total human-annotated evaluations
- Difficulty levels: 18 Easy, 20 Medium, 12 Hard
- Topics: Percentages, Ratio & proportion, Averages, 
    Profit & loss, simple & compound interest, Time & work, 
    Time, speed & distance, Algebra, Geometry, Number system.

## Scoring Rubric
Each response is scored on three dimensions (0-5 each):
- Correctness Score: Accuracy of the final answer and steps
- Reasoning Score: Logical validity of the working shown
- Clarity Score: Structure and readability of the response
- Final Score: Weighted formula = (Correctness x 0.5 + Reasoning x 0.3 + Clarity x 0.2) x 20
- Gives a score from 0 to 100.

## Error Types
No Error, Calculation Error, Conceptual Error, 
Methodology Error, Incomplete Solution, Sign Error, 
Unit Error, Symbol Error, Incomplete Answer, Multiple Errors

## Files
- dataset.csv — main evaluation dataset (150 rows)
- rubric.md — full scoring rubric with examples
- methodology.md — data collection methodology

## Dataset Columns
| Column                | Description                              |
| Question ID           | Unique identifier (M001 – M050)          |
| Model Name            | GPT-4o, Claude, or Gemini                |
| Topic                 | Math topic category                      |
| Difficulty            | Easy, Medium, or Hard                    |
| Question              | The math problem text                    |
| Correct Answer        | Ground truth answer (manually solved)    |
| Verified Answer       | Cross-verified answer (Wolfram Alpha)    |
| AI Response           | Full LLM-generated solution (plain text) |
| Correctness Score     | 0 – 5                                    |
| Reasoning Score       | 0 – 5                                    |
| Clarity Score         | 0 – 5                                    |
| Error Type            | One of 10 error type categories           |
| Final Score           | 0 – 100 (weighted formula)               |
| Evaluator Explanation | One-sentence human justification         |

## Author
**N B V BHARATH** — Independent AI Evaluation Researcher
