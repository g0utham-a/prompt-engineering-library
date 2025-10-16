# Prompt Template: The Sentiment Analyzer 

## Development Log - V1 - Basic Extraction
## Core Prompt
Analyze the following customer review, delimited by triple backticks. Identify the product being reviewed and the sentiment (positive or negative). Provide the output in JSON format with the keys "product" and "sentiment"

## Input - Review Negative
"This coffee maker is a disaster. The carafe drips everywhere when I pour, and the 'auto-shutoff' feature just randomly turns the machine off mid-brew. I'm going back to my old Mr. Coffee. Complete waste of money."

## Model
gpt-4.1-mini

## Output
{
"product": "coffee maker",
"sentiment": "negative"
}


## Input - Review Positive
"I was skeptical about a subscription for socks, but I'm a convert. The quality is amazing, they feel great, and a fresh pair just shows up at my door every month without me having to think about it. The onboarding was super easy too. Highly recommend."

## Model
gpt-4.1-mini

## Output
{
"product": "sock subscription service",
"sentiment": "positive"
}


## Development Log - V2 Advanced Extraction with Actionable Insight
## Core Prompt
Analyze the following customer review, delimited by triple backticks. Identify:
- The product being reviewed,
- The sentiment of the review (positive or negative),
- The root cause of the sentiment (summarized in one clear sentence).

Carefully read and reason through the review to extract the required information. Only after completing this analysis, present your results in a JSON format with the keys:
- "product"
- "sentiment"
- "root_cause_summary" (as a single sentence).

# Steps
1. Carefully read the review within the triple backticks.
2. Determine the product being reviewed.
3. Assess the overall sentiment (positive or negative).
4. Analyze the text to identify the core reason why the reviewer feels this way, and express it in a single, clear sentence.
5. Present your response in the specified JSON format.

# Output Format

Respond in JSON (do not use code blocks), structured as follows:
{
  "product": "[Name or description of the product]",
  "sentiment": "[positive or negative]",
  "root_cause_summary": "[A single sentence summarizing the root cause of the sentiment]"
}

# Example

Review:
```
I ordered the NoiseBlocker headphones and while the sound quality is great, the ear pads started peeling after only two weeks. Really disappointed.
```
Output:
{
  "product": "NoiseBlocker headphones",
  "sentiment": "negative",
  "root_cause_summary": "The ear pads started peeling after only two weeks of use."
}

# Notes
- The "root_cause_summary" should be concise and focus only on the main reason for the sentiment, not on general opinions or unrelated details.
- Always reason through the review before formulating your final output.

## Input - Review Negative
"This coffee maker is a disaster. The carafe drips everywhere when I pour, and the 'auto-shutoff' feature just randomly turns the machine off mid-brew. I'm going back to my old Mr. Coffee. Complete waste of money."

## Model
gpt-4.1-mini

## Output
{
"product": "coffee maker",
"sentiment": "negative",
"root_cause_summary": "The carafe drips when pouring and the 'auto-shutoff' randomly turns the machine off mid-brew."
}


## Input - Review Positive
"I was skeptical about a subscription for socks, but I'm a convert. The quality is amazing, they feel great, and a fresh pair just shows up at my door every month without me having to think about it. The onboarding was super easy too. Highly recommend."

## Model
gpt-4.1-mini

## Output
{
"product": "sock subscription service",
"sentiment": "positive",
"root_cause_summary": "The socks are high quality and comfortable, and the easy onboarding plus automatic monthly delivery make the service very convenient."
}

