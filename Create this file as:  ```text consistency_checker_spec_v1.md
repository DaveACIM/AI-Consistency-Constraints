# Consistency Checker (CC) v1

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

