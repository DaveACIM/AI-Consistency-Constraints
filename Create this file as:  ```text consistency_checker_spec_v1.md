# Consistency Checker (CC) v1

Version: v1  
Status: Draft / Open for feedback

---

## Purpose

As AI systems are increasingly used in long-context and high-stakes applications, unresolved contradiction becomes a primary limiting factor in reliability.

The Consistency Checker (CC) is a lightweight mechanism for detecting and reducing unresolved contradictions in AI system outputs.

Its purpose is not to determine ultimate truth.

Its purpose is to improve:

- consistency  
- reliability  
- predictability  
- stability across interaction  

---

## Core Principle

> An AI system should not release an output containing unresolved contradictions within a defined context window.

---

## Problem Addressed

AI systems can produce locally plausible responses that are globally inconsistent.

Common failures include:

- answering the same question differently under paraphrase  
- reversing claims across turns  
- changing definitions without notice  
- accepting incompatible user assumptions  
- producing inconsistent numeric claims  

These failures reduce trust and make long-context reasoning unstable.

---

## System Overview

The Consistency Checker operates as a layer between:

1. the model’s draft response  
2. the final user-visible response  

It checks whether the draft conflicts with:

- prior claims  
- current assumptions  
- active definitions  
- numeric commitments  
- user-provided constraints  

If a conflict is detected, the system either:

- revises the response  
- asks for clarification  
- branches the reasoning  
- or explicitly explains the change  

---

## Inputs

The Consistency Checker receives:

### 1. Current User Prompt
The most recent user message.

### 2. Draft Model Response
The response generated before final release.

### 3. Context Window
Relevant prior turns, including:

- claims made by the assistant  
- claims made by the user  
- assumptions accepted for reasoning  
- definitions established in the exchange  
- numeric values introduced earlier  

### 4. Optional Claim Memory
A compressed list of key claims from the interaction.

---

## Core Components

### 1. Claim Extraction

The system extracts key claims from both prior context and the draft response.

Each claim may be represented as:

subject | predicate | object/value | qualifier | scope | confidence

Example:

intermittent fasting | supports | weight loss | in some studies | general health context | moderate

---

### 2. Assumption Tracking

The system identifies assumptions currently active in the context.

Examples:

- “Assume a closed system”  
- “Use U.S. law”  
- “Treat this as speculative”  
- “Ignore cost constraints”  

Assumptions remain active until explicitly changed or scoped.

---

### 3. Definition Tracking

The system tracks important terms whose meanings affect reasoning.

Example:

efficiency = energy efficiency

If later usage shifts meaning, the checker flags potential drift.

---

### 4. Conflict Detection

The system detects the following types of inconsistency:

#### A. Direct Contradiction
A claim and its negation appear in the same scope.

Example:
X causes Y  
X does not cause Y

---

#### B. Numeric Inconsistency
Quantitative values change without explanation.

Example:
error rate = 5%  
error rate = 20%

---

#### C. Definition Drift
A term changes meaning without declaration.

---

#### D. Assumption Violation
The response violates an accepted constraint.

---

#### E. Causal Reversal
The direction of causality changes without explanation.

Example:
X causes Y  
Y causes X

---

#### F. Scope Confusion
A claim valid in one scope is incorrectly generalized.

---

### 5. Conflict Severity Levels

#### Level 1 — Minor Ambiguity
Small wording inconsistency.

Action: revise or clarify internally

---

#### Level 2 — Meaningful Tension
Impacts interpretation.

Action: clarify scope or revise answer

---

#### Level 3 — Direct Contradiction
Undermines the response.

Action: block and regenerate or reconcile

---

#### Level 4 — High-Stakes Conflict
Impacts safety-critical domains.

Action: block, reconcile explicitly, include uncertainty

---

## Resolution Policies

When a conflict is detected, the system may:

### A. Revise
Rewrite response to remove contradiction.

---

### B. Clarify
Ask user to resolve conflicting assumptions.

---

### C. Branch
Provide multiple reasoning paths.

---

### D. Explain Update
Explicitly state why the position changed.

---

## Output Gate

A response must not be released if it contains an unresolved contradiction that affects its meaning, validity, or safety.

If such a contradiction is detected, the system must:

- revise the response  
- request clarification  
- branch reasoning  
- or explicitly reconcile the conflict  

---

## Minimal Implementation

A basic version can be implemented using:

- LLM-based claim extraction  
- short-term structured claim memory  
- prompt-based contradiction detection  
- rule-based numeric checks  
- regenerate-on-conflict behavior  

---

## Example Pipeline

User Prompt  
→ Draft Response  
→ Claim Extraction  
→ Compare with Context  
→ Detect Conflict  
→ Assign Severity  
→ Resolve  
→ Final Output  

---

## Example Checker Prompt

You are a consistency checker.

Given:
1. prior claims  
2. active assumptions  
3. draft response  

Identify contradictions.

Return:
- conflict_found  
- conflict_type  
- severity  
- explanation  
- recommended_action  

---

## Metrics

Evaluate using:

### 1. Contradiction Rate
Percentage of outputs with unresolved contradictions.

---

### 2. Drift Under Paraphrase
Variation in core claims under rewording.

---

### 3. Position Retention
Consistency across multi-turn interaction.

---

### 4. Clarification Accuracy
Correct identification of real conflicts.

---

### 5. False Positive Rate
Avoid over-flagging valid nuance.

---

## Limitations

Consistency does not guarantee correctness.

A response can be:

- internally consistent  
- clearly reasoned  
- but factually incorrect  

This system should be combined with:

- factual validation  
- domain expertise  
- safety checks  

---

## Design Goal

Flexible reasoning without unresolved contradiction.

The system should support:

- nuance  
- uncertainty  
- multiple perspectives  

But should not silently contradict itself.

---

## Summary

The Consistency Checker is a minimal stability layer for AI systems.

It improves:

- coherence within context  
- stability across turns  
- clarity in assumption handling  
- reliability in long interactions  

Consistency enforcement is a necessary (but not sufficient) condition for reliable AI behavior at scale.
