# APA System One Cookbooks  cookbook index

A collection of battle-tested, copy-pasteable architectural patterns and code recipes for building autonomous AI personas, multi-agent systems, and decision pipelines with **Jev** and TypeSafe System One models.

Maintained by **APA (AIPersona Academy)**.

---

## Available Cookbooks

| Cookbook | Problem Solved | Key Primitives |
| :--- | :--- | :--- |
| **[1. Persona State Routing](persona-state-routing.md)** | Route autonomous brand personas across states without LLM chat hallucinations | `Choice`, `Score` |
| **[2. Social Sentiment & Policy Guardrails](social-sentiment-guardrails.md)** | Sub-100ms content safety scoring, toxic prompt screening, and confidence gating | `Noul`, `Score` |
| **[3. Buyer Persona Pain-Point Scoring](buyer-persona-scoring.md)** | Extract customer objections, score pain-point severity, and classify purchase intent | `Choice`, `Noul` |

---

## Core Principles

1. **Decouple Thinking from Doing**: Use generative models (Claude, GPT, Gemini) for creative drafting and natural language synthesis. Use System One models (**Jev**) for all control-plane routing, branching, and policy enforcement.
2. **Confidence-Gated Actions**: Never act blindly on probabilities. Always gate high-stakes operations behind calibrated confidence thresholds.
3. **Speculative Fan-out**: Execute atomic evaluations in parallel against shared state to achieve sub-second end-to-end agent turns.
