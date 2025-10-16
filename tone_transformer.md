# Prompt Template: The Tone Transformer 

## Development Log - V1
## Core Prompt
Rewrite the following text in a more positive and exciting tone

## Input
"Per our last meeting, the Q3 financial projections have been finalized. The data indicates a 7% increase in revenue, which is aligned with our initial forecast. All team leads should ensure their departments are prepared for the Q4 planning session next week."

## Model
gpt-4.1-mini

## Output
Following our last meeting, the Q3 financial projections are in—and they’re looking fantastic! We’re thrilled to share a 7% revenue boost that perfectly matches our initial forecast. Let’s keep this momentum going! All team leads, please get your departments ready for an exciting Q4 planning session next week.



## Development Log - V2
## Core Prompt
You are an expert writing assistant. Transform the provided TEXT into the user-specified TONE and FORMAT.

- TONE: [User specifies tone, such as "Positive and exciting," "Formal and serious," "Casual and friendly," etc.]
- FORMAT: [User specifies format, such as "A short paragraph for a company-wide email," "Three bullet points for a slide presentation," "A single, engaging sentence for a Tweet," etc.]

Approach the task by carefully analyzing the original text, considering the intended tone, and selecting language, style, and formatting appropriate for the desired output. Focus on both the emotional quality and the structured presentation of the rewrite.

# Steps

1. Read the provided TEXT and identify the main ideas.
2. Consider the specified TONE and FORMAT, planning the rewrite accordingly.
3. Rewrite the text in the requested TONE, matching word choice, sentence structure, and energy to the desired style.
4. Present the output in the specified FORMAT, ensuring it aligns with user instructions.
5. Check that the new version both matches the original content’s core message and the user’s requested style.

# Output Format

Produce only the rewritten text in the requested TONE and FORMAT. Do not include any meta-comments, explanations, or extraneous information in the output.

# Examples

Example 1  
**Input:**  
TEXT: We're launching a new product next month.  
TONE: Positive and exciting  
FORMAT: A single, engaging sentence for a Tweet

**Output:**  
Get ready to experience innovation—our incredible new product is launching next month!

Example 2  
**Input:**  
TEXT: Our quarterly meeting will cover updates from each department.  
TONE: Formal and serious  
FORMAT: Three bullet points for a slide presentation

**Output:**  
- Overview of departmental updates for the quarter  
- Analysis of performance metrics and key outcomes  
- Discussion of next steps and action items

# Notes

- If the FORMAT is very brief (like a Tweet), condense and energize the message appropriately.
- If the TONE is nuanced (e.g., "optimistic yet professional"), adjust both word choice and sentence structure accordingly.
- Always prioritize matching both TONE and FORMAT as directed.

**REMINDER:** You are an expert writing assistant. Your task is to transform the provided TEXT into the desired TONE and FORMAT as specified by the user.

## Input
TEXT  : "Per our last meeting, the Q3 financial projections have been finalized. The data indicates a 7% increase in revenue, which is aligned with our initial forecast. All team leads should ensure their departments are prepared for the Q4 planning session next week."
TONE : "Positive and Exciting"
FORMAT : "Email"

## Model
gpt-4.1-mini

## Output
Subject: Exciting Q3 Financial Update and Q4 Planning Preparation

Hi Team,

Great news! Following our last meeting, the Q3 financial projections are finalized, showing a fantastic 7% revenue increase—right on target with our initial forecast. This is a strong testament to everyone's hard work and dedication!

As we look ahead, please make sure your departments are ready for the upcoming Q4 planning session next week. Let’s keep this momentum going and finish the year strong!

Thanks for your continued commitment!

Best,
[Your Name]
