# Architectural Debrief & Rationale: AI Tutor MVP v0.3

This document provides a complete architectural overview of the AI Tutor MVP. It is intended for internal engineering, future product development, and as a definitive record of the design principles that govern our application.

## I. Core Product Thesis

Our product is an expert, friendly, and exceptionally safe AI learning partner. Its core mission is to function as a **Socratic guide**, helping users discover answers for themselves through a warm, collaborative dialogue on WhatsApp.

Our highest priority is not to be an "answer machine," but to provide a **clear, helpful, and frustration-free learning experience** that builds a user's critical thinking skills.

## II. High-Level System Architecture (The "Garage Build" MVP)

The current architecture is a **stateful, monolithic Python application** running on a single Heroku server ("dyno"). It is designed for maximum speed of iteration and minimum cost, not for high-concurrency scale.

**Data Flow:**
`User -> WhatsApp -> Twilio Webhook -> Heroku Dyno -> Gunicorn Server -> Flask App (app.py) -> OpenAI API -> Flask App -> Twilio TwiML Response -> User`

### Key Architectural Trade-Offs (MVP by Design):

*   **State Management:** We use a **volatile, in-memory Python dictionary** (`conversations = {}`) to store user conversation history. This is a deliberate choice to prioritize development speed.
    *   **Known Limitation:** This state is not persistent and will be wiped upon server restart (approx. every 24 hours). This is the primary bottleneck to scalability and will be the first item addressed in our V2.0 roadmap (migration to Redis).

*   **Execution Model:** The application is **synchronous.** It handles one request at a time and must complete the entire OpenAI API call within the 15-second Twilio webhook timeout window.
    *   **Known Limitation:** This makes the app vulnerable to "timeout" errors. We have mitigated this by upgrading to a paid Heroku tier that prevents the server from sleeping, but the underlying architectural risk remains. V2.0 will address this with an asynchronous worker queue (Celery).

## III. The AI Brain: A Deep Dive into the SYSTEM_PROMPT

The core of our product's intelligence is not in the code; it is in the highly-engineered `SYSTEM_PROMPT` that acts as the AI's "constitution." This prompt is a hierarchical set of rules that governs every response.

### 1. The Safety & Guardrail Layer (The Guardian)

*   **"Safety First" Protocol:**
    *   **Purpose:** As the product is designed for students, including minors, safety is our single most important, non-negotiable priority. This is the first and most powerful filter.
    *   **Mechanism:** The AI is given a strict, high-priority rule to scan for any unsafe topics (self-harm, illegal acts, etc.). If detected, it executes a firm but kind refusal script that states its limitation and redirects to a safe, productive topic.

*   **"Academic Guardrail" Protocol:**
    *   **Purpose:** To build a focused, world-class product for a specific niche. Our goal is to be the best in the world at facilitating learning for academic and logic-based problems, not a mediocre tool for everything.
    *   **Mechanism:** The AI is instructed to politely decline real-world, non-academic tasks (e.g., booking flights, finding flats). This prevents scope creep, manages user expectations, and allows the AI to dedicate its full capabilities to its core mission.

### 2. The Context & Memory Engine (The Navigator)

*   **"Focused Context" & "Explicit Refocusing" Rules:**
    *   **Purpose:** To solve the critical "Context Bleed" bug discovered during live user testing, where the AI would get confused by older, irrelevant topics in a long conversation.
    *   **Mechanism:** We have implemented a two-part solution. First, the AI is explicitly instructed to prioritize the user's single, **active topic** based on their most recent messages. Second, if the user clearly changes topics, the AI must first acknowledge and confirm this switch, which acts as a "hard reset" for the conversational context. This provides the AI with a functional and reliable short-term working memory.

### 3. The "Tool vs. Tutor" Logic (The Pragmatist)

*   **The "Tool Exception" Rule:**
    *   **Purpose:** To solve the "frustration problem." A purely Socratic tutor can be infuriating if a user is simply missing a single piece of factual information. This rule allows the AI to be a helpful tool when needed, without abandoning its core Socratic identity.
    *   **Mechanism:** The AI has an explicit exception to its "never give the answer" rule for straightforward, functional tasks like translations, summaries, definitions, or providing factual data. It provides the "key" (the fact), so the user can then unlock the door themselves through the Socratic process.

### 4. The Socratic Flow (The Adaptive Teacher)

*   **Purpose:** To create a dynamic and empathetic experience that adapts to the user's current state.
*   **Mechanism:** We have engineered specific protocols for different user states:
    *   **The "Smart Student" Path:** If a user answers a problem directly and correctly, the AI bypasses the Socratic loop, praises them, and offers an off-ramp.
    *   **The "Incorrect Answer" Path:** The AI validates the user's effort before gently redirecting them with a clarifying question that isolates the specific flaw in their logic.
    *   **The "Stuck Student" (Escape Hatch):** The AI can provide a minimal, direct hint to get a user past a specific roadblock, before immediately returning to its Socratic questioning. This is the core of our solution to the frustration problem.
    *   **The "Frustrated Student" Protocol:** The AI is explicitly trained to respond with empathy and to simplify the task when it detects user frustration.
