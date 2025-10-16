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

## Input 1
TEXT  : "Per our last meeting, the Q3 financial projections have been finalized. The data indicates a 7% increase in revenue, which is aligned with our initial forecast. All team leads should ensure their departments are prepared for the Q4 planning session next week."
TONE : "Positive and Exciting"
FORMAT : " An exciting paragraph for a company-wide email."

## Model
gpt-4.1-mini

## Output
Great news from our recent meeting—Q3 financial projections are finalized, showing an exciting 7% boost in revenue that perfectly matches our optimistic forecast! This achievement reflects our collective hard work and momentum. Now, as we gear up for next week’s Q4 planning session, all team leads are encouraged to get their departments ready to build on this success and drive even greater results together!


## Input 2
TEXT  : "Per our last meeting, the Q3 financial projections have been finalized. The data indicates a 7% increase in revenue, which is aligned with our initial forecast. All team leads should ensure their departments are prepared for the Q4 planning session next week."
TONE : "Positive and Exciting"
FORMAT : " An urgent set of bullet points for a presentation."

## Model
gpt-4.1-mini

## Output
- Great news! Q3 financial projections are finalized with a promising 7% revenue increase!
- This growth matches our optimistic initial forecast—our strategy is working!
- Attention all team leads: Get your departments ready for the exciting Q4 planning session next week!
Let’s keep this momentum going and make Q4 even more successful!
