# Principles of Prompting

## 1. Write Clear and Specific Instructions

**Key idea:** Clear ≠ short. Longer prompts often provide better context to the model.

### Tactics
- **Use delimiters** such as `````` ```
- **Ask for structured output** like JSON, XML tags, or tables.
- **Ask the model to verify** whether given conditions or constraints are met.
- **Use few-shot prompting** by showing a few examples of the desired output before asking the main question.

***

## 2. Give the Model Time to Think

### Tactics
- **Specify the steps** needed to complete a task to encourage reasoning.
- **Ask the model to generate its own reasoning or plan** before providing the final answer.

***

## Bonus: Reduce Hallucinations

- Instruct the model to **first identify relevant information**.
- Then ask it to **formulate the answer only based on that verified information**.
