# Prompt Template: The Sentiment Analyser

## Core Prompt
Identify the following items from the review text: 
- Item purchased by reviewer
- Company that made the item
- Sentiment (positive or negative)
- Is the reviewer expressing anger? (true or false)
- Root cause of user's sentiment


## Constraints and Directives
- The review is delimited with triple backticks. \
- Format your response as a JSON object with \
- "Sentiment", "Anger", Root Cause", "Item" and "Brand" as the keys.
- If the information isn't present, use "unknown" \
as the value.
- Make your response as short as possible.
- Format the Anger value as a boolean.

## Core Prompt Improved via ChatGPT Playground
Extract the following items from the review text provided within triple backticks:

- The item purchased by the reviewer (as "Item")
- The company or brand that made the item (as "Brand")
- The overall sentiment expressed by the reviewer ("positive" or "negative"; as "Sentiment")
- Whether the reviewer is expressing anger (as boolean "Anger": true or false)
- The main root cause for the user's sentiment (as "Root Cause")

If any information is not present in the review, return "unknown" as the value for that field. For the "Anger" field, always use either true or false (do not use "unknown").

Your response should be as short as possible.

# Output Format

Respond with a single JSON object using the keys: "Item", "Brand", "Sentiment", "Anger", and "Root Cause". Make sure the values match the instructions above.

# Example

Input review:
```
I am so frustrated! My brand new ACME Toaster broke after one week.
```

Output:
{
  "Item": "Toaster",
  "Brand": "ACME",
  "Sentiment": "negative",
  "Anger": true,
  "Root Cause": "broke after one week"
}

# Notes

- Only use the information clearly present in the review text.
- For missing values, always output "unknown" (except for "Anger": must be true or false).
- Do not provide any commentary or explanation, only the JSON output.

## Development Log - V1
## Review (Negative)
"This coffee maker is a disaster. The carafe drips everywhere when I pour, and the 'auto-shutoff' feature just randomly turns the machine off mid-brew. I'm going back to my old Mr. Coffee. Complete waste of money."
## Model
gpt-4.1-mini

## Output
{
"Item": "coffee maker",
"Brand": "unknown",
"Sentiment": "negative",
"Anger": true,
"Root Cause": "carafe drips and auto-shutoff turns machine off mid-brew"
}

## Development Log - V2
## Review (Positive)
"I was skeptical about a subscription for socks, but I'm a convert. The quality is amazing, they feel great, and a fresh pair just shows up at my door every month without me having to think about it. The onboarding was super easy too. Highly recommend."## Model
gpt-4.1-mini

## Output
{
  "Item": "socks",
  "Brand": "unknown",
  "Sentiment": "positive",
  "Anger": false,
  "Root Cause": "quality is amazing and easy subscription"
}




