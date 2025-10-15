# prompt-engineering-library
Principles of prompting
1. Write clear and specific instructions
2. Give model time to think

1. Write clear and specific instructions
  First and foremost: clear =! short. long prompts often give better context to the model
  Tactic 1: Use delimiters lile ```, """, etc
  Tactic 2: Ask for a structured output like JSON, XML tags etc
  Tactic 3: Ask the model to see if the conditions are met
  Tactic 4: Few shot programming

2. Give model time to think
   Tactic 1: Specify the steps required to complete a task
   Tactic 2: Ask the model to comeup with its own solution before answering

Bonus: Reducing hallucainations: Ask to model to first find relevant information and then answer the question based on the relevant information
   
