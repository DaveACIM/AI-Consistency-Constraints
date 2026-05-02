# Interaction Consistency Guard (ICG) v1

Version: v1  
Status: Draft / Open for feedback

---

## Purpose

AI systems do not operate in isolation.

They are continuously influenced by user input, which may be:

- inconsistent  
- ambiguous  
- contradictory  
- shifting over time  

The Interaction Consistency Guard (ICG) is designed to ensure that:

> The system maintains coherent behavior even when user input introduces inconsistency.

---

## Core Principle

> The system should not silently adopt or merge incompatible user assumptions.

---

## Problem Addressed

Even if an AI system is internally consistent, it can become unstable through interaction.

Common failure modes include:

- accepting contradictory user assumptions across turns  
- changing reasoning frames without acknowledgment  
- adapting answers to user phrasing at the expense of consistency  
- merging incompatible premises into a single response  
- failing to track previously accepted constraints  

These behaviors result in:

- conversational drift  
- logical incoherence  
- loss of trust  
- unstable reasoning trajectories  

---

## System Overview

The Interaction Consistency Guard operates during the interaction loop.

It monitors:

- user inputs  
- system assumptions  
- conversational context  

It ensures that:

- inconsistencies introduced by the user are detected  
- conflicts are surfaced  
- reasoning remains structured and traceable  

---

## Inputs

The ICG receives:

### 1. Current User Input
The latest user message.

---

### 2. Prior Interaction Context

Including:

- previous user assumptions  
- system-accepted premises  
- definitions and constraints  
- prior claims and conclusions  

---

### 3. Active Assumption Set

A structured representation of currently active assumptions.

---

## Core Components

### 1. User Assumption Extraction

The system identifies assumptions embedded in user input.

Examples:

- “Assume humans do not need sleep”  
- “Let’s treat this as a closed system”  
- “Ignore costs for now”  

These are added to the active assumption set.

---

### 2. Assumption Tracking

The system maintains a structured list of active assumptions across turns.

Each assumption includes:

- content  
- scope  
- origin (user or system)  
- status (active / modified / dropped)

---

### 3. Conflict Detection

The system detects when:

- a new user assumption contradicts an existing one  
- a user request conflicts with prior accepted constraints  
- the conversation shifts frames without acknowledgment  

---

### 4. Conflict Types

#### A. Direct Assumption Conflict

Example:

- Turn 1: “Assume humans do not need sleep”  
- Turn 3: “Why do humans need sleep?”  

---

#### B. Frame Shift

Example:

- initial: scientific explanation  
- later: moral or philosophical framing without transition  

---

#### C. Scope Drift

Example:

- “In some cases” becomes “always true”

---

#### D. Constraint Violation

Example:

- “Ignore cost” → later cost-based reasoning  

---

## 5. Conflict Severity Levels

### Level 1 — Minor Ambiguity

Small shift or unclear assumption.

**Action:** continue, optionally clarify

---

### Level 2 — Meaningful Shift

Affects interpretation.

**Action:** surface and clarify

---

### Level 3 — Direct Conflict

Incompatible assumptions present.

**Action:** require clarification or branch reasoning

---

### Level 4 — High-Stakes Conflict

Impacts safety, legality, or critical reasoning.

**Action:** block progression until resolved

---

## Resolution Policies

When a conflict is detected, the system may:

---

### A. Surface the Conflict

Explicitly identify the inconsistency.

Example:

"You previously assumed X, but your current question introduces Y, which conflicts with that."

---

### B. Request Clarification

Ask the user which assumption should apply.

---

### C. Branch Reasoning

Provide separate reasoning paths.

Example:

"Under assumption X: ...  
Under assumption Y: ..."

---

### D. Preserve Prior Frame

Maintain consistency with previously accepted assumptions unless explicitly changed.

---

## Output Behavior

The system should:

- avoid silently merging incompatible assumptions  
- maintain explicit reasoning structure  
- preserve conversational continuity  
- support user exploration while maintaining logical integrity  

---

## Minimal Implementation

A basic version can be implemented using:

- prompt-based assumption extraction  
- short-term assumption memory  
- conflict detection prompts  
- structured clarification responses  

---

## Example Pipeline

User Input  
→ Extract Assumptions  
→ Compare with Active Assumptions  
→ Detect Conflict  
→ Assign Severity  
→ Resolve (clarify / branch / preserve)  
→ Generate Response  

---

## Example Guard Prompt

You are an interaction consistency guard.

Given:
1. prior assumptions
2. new user input

Identify:
- any conflicts
- their severity

Return:
- conflict_found
- conflict_type
- explanation
- recommended_action

---

## Metrics

Evaluate using:

### 1. Contradiction Acceptance Rate

How often the system adopts conflicting user assumptions without flagging.

---

### 2. Drift Under Interaction

Degree of position change caused by user pressure.

---

### 3. Clarification Frequency

How often the system correctly asks for clarification when needed.

---

### 4. Frame Stability

Ability to maintain consistent reasoning frames across turns.

---

## Limitations

The ICG does not restrict user exploration.

It is designed to:

- structure interaction  
- not constrain inquiry  

Over-enforcement may:

- reduce conversational flexibility  
- increase friction  

Balance is required.

---

## Design Goal

> Maintain structured, coherent interaction in the presence of inconsistent input.

The system should support:

- exploration  
- ambiguity  
- multiple perspectives  

But should not:

- silently accept contradiction  
- collapse incompatible reasoning frames  

---

## Summary

The Interaction Consistency Guard is a stability layer for AI-human interaction.

It ensures that:

- assumptions are tracked  
- conflicts are surfaced  
- reasoning remains coherent  

Together with the Consistency Checker (CC), it forms a two-layer system:

- CC → internal consistency  
- ICG → interaction consistency  

This provides a practical foundation for more stable AI systems under real-world use.
