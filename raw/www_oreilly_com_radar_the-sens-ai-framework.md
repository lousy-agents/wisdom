---
source_url: "https://www.oreilly.com/radar/the-sens-ai-framework/"
type: webpage
title: "The Sens-AI Framework: Teaching Developers to Think with AI"
captured_at: 2026-06-29T13:05:21.852000+00:00
contributor: "zpratt"
author: "Andrew Stellman"
---

# The Sens-AI Framework: Teaching Developers to Think with AI

Source: https://www.oreilly.com/radar/the-sens-ai-framework/

---

The Sens-AI Framework: Teaching Developers to Think with AI

By Andrew Stellman

This article introduces the Sens-AI Framework, a practical 5-step approach to using AI tools effectively for real coding work. The framework was developed by Andrew Stellman from his experience updating *Head First C#* to help readers develop both coding and AI skills. It is also the foundation of his O'Reilly report, *Critical Thinking Habits for Coding with AI*, and an ongoing O'Reilly Radar series.

## The Learning Gap

AI coding tools like GitHub Copilot, ChatGPT, and Claude are rapidly becoming indispensable for developers. However, developers using AI often run into situations where the model gets stuck in repetitive loops (rehash loops), produces plausible but incorrect code, or makes unfounded assumptions. The Sens-AI framework addresses the "learning gap" many developers face when simultaneously learning programming and how to think with AI.

A particular risk is the **cognitive shortcut paradox**: overreliance on AI output, especially by less experienced developers, can short-circuit the learning process and prevent them from developing the problem-solving experience required for good engineering decisions later.

## The Five Core Habits

The Sens-AI Framework teaches developers five key habits for effectively leveraging AI in development:

### 1. Context
Always understand the environment, purpose, and limitations of your coding task and AI tool before you start. Set clear goals not just for the code, but for the learning process itself. Carefully review AI-generated code before accepting it—understand what it does and why.

### 2. Research
Treat prompting as an act of research—gather background, verify documentation, and use AI as a partner to explore solution spaces instead of just seeking one-off answers. Don't accept AI output at face value; investigate edge cases, alternative approaches, and the rationale behind suggestions.

### 3. Problem Framing
Clearly define problems for both yourself and the AI. Effective prompts mirror requirements engineering—good prompt engineering is good requirements practice. Clarify your intent before diving into detail. Are you asking for structure? Behavior? Tradeoffs? Use personas, constraints, and examples to pin down vague terms.

### 4. Refining
Iteratively refine both code and prompts. Recognize when the AI is stuck in a **rehash loop**—where the model keeps generating similar, incomplete, or incorrect answers in response to repeated prompts—and deliberately break free, adjusting your approach or constraints. Every revision helps you learn more about the model, the task, and the question you're actually trying to ask.

### 5. Critical Thinking
Always validate, test, and critique the AI's answers. Build the habit of not accepting output at face value and develop judgment about when to trust, adapt, or discard what the AI suggests. Passing tests are evidence, not proof. AI tools may sometimes produce code that doesn't compile or work as expected—you're in charge.

## The Rehash Loop

A central concept in the framework is the **rehash loop**: when AI keeps generating variations of the same incomplete or incorrect approach in response to repeated prompts. This trap stalls progress and prevents real learning or productivity gains. The framework teaches developers to recognize when they're in a rehash loop and to stop, step back, and reapply the five key habits—especially reframing the problem or shifting context.

## AI-Resistant Technical Debt

The Sens-AI Framework also addresses **AI-resistant technical debt**: unmaintainable code structures created by over-automation or uncritical acceptance of AI-generated code. Developers must review AI output carefully and stay engaged with their work, maintaining control and understanding rather than becoming passive consumers of AI output.

## The Framework in Practice

The framework is actively used in *Head First C#* (O'Reilly) and as a training methodology in developer upskilling programs, including an O'Reilly live training course. Key practices include:

- Setting clear learning goals alongside coding goals
- Asking the AI what assumptions it is making and what information is missing
- Using follow-up prompts to explore edge cases and alternative solutions
- Asking the AI to explain its refactoring decisions and the principles it applied
- Treating AI as a research partner rather than an oracle

## Application to Teams

The framework is as much about team culture as individual practice. Team leads and instructors are encouraged to help developers adopt these habits to ensure skills growth alongside AI adoption. The **AI Teaching Toolkit** extension of the series provides practical guidance for teams integrating these practices.

## Related Resources

- *Critical Thinking Habits for Coding with AI* (O'Reilly, 2025) by Andrew Stellman
- O'Reilly Radar series: "The Sens-AI Framework" (https://www.oreilly.com/radar/the-sens-ai-framework/)
- GitHub repository: https://github.com/andrewstellman/sens-ai-course
- *Head First C#* (5th Edition, O'Reilly)
- Related articles in the series: "The Rehash Loop", "The Cognitive Shortcut Paradox", "The AI Teaching Toolkit: Practical Guidance for Teams"
