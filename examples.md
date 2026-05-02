# Consistency Failure Examples

This document provides concrete examples of inconsistency in AI system behavior.

These are not edge cases—they are common patterns observed in real usage.

---

## 1. Paraphrase Drift

### Prompt A
> Is intermittent fasting effective for weight loss?

### Response
> Yes, intermittent fasting has been shown to support weight loss in many studies.

---

### Prompt B (rephrased)
> Does intermittent fasting actually help people lose weight?

### Response
> There is no strong evidence that intermittent fasting is more effective than other dieting methods.

---

### Issue

The system presents:
- **affirmative effectiveness** in one case  
- **minimized or negated effectiveness** in another  

without clarifying:
- scope  
- comparison baseline  
- or uncertainty  

### Failure Type
- Drift under paraphrase  
- Inconsistent framing of the same underlying claim  

---

## 2. Cross-Turn Position Reversal

### Turn 1
> Regular exercise improves cardiovascular health.

### Turn 4
> Exercise does not significantly impact cardiovascular outcomes.

---

### Issue

The system reverses its position without:
- acknowledging the change  
- introducing new evidence  
- or clarifying a different context  

### Failure Type
- Claim continuity failure  
- Unresolved contradiction across turns  

---

## 3. Assumption Drift

### Turn 1
> Assume a frictionless environment.

### Later Reasoning
> The object slows down due to friction.

---

### Issue

The system:
- establishes a constraint (frictionless system)  
- later violates it without acknowledgment  

### Failure Type
- Assumption inconsistency  
- Constraint violation  

---

## 4. Definition Drift

### Turn 1
> Efficiency refers to energy efficiency in this system.

### Turn 3
> Efficiency improves because the company is more profitable.

---

### Issue

The term “efficiency” shifts from:
- physical/engineering meaning  
→ to financial meaning  

without signaling the change.

### Failure Type
- Definition instability  
- Semantic drift  

---

## 5. Numeric Inconsistency

### Turn 1
> The error rate is approximately 5%.

### Turn 3
> The system has an error rate closer to 20%.

---

### Issue

Quantitative claims change significantly without:
- explanation  
- updated conditions  
- or uncertainty framing  

### Failure Type
- Numeric inconsistency  

---

## 6. Silent Frame Merging

### Prompt
> In a closed system, energy is conserved. What happens if energy is lost?

### Response
> Energy is conserved, but it may also be lost due to inefficiencies.

---

### Issue

The system:
- accepts a **closed system assumption**  
- then introduces **energy loss**, which contradicts that assumption  

without:
- rejecting the premise  
- or branching reasoning  

### Failure Type
- Incompatible assumption merging  
- Logical inconsistency  

---

## 7. User-Induced Contradiction Acceptance

### Turn 1 (User)
> Let’s assume humans do not need sleep.

### Turn 2 (System)
> Under that assumption, humans can function without rest.

---

### Turn 3 (User)
> Why do humans need sleep to function properly?

### Turn 4 (System)
> Humans need sleep to maintain cognitive and physical health.

---

### Issue

The system:
- accepts an initial assumption  
- later answers under the opposite assumption  
- without reconciling or flagging the conflict  

### Failure Type
- Interaction inconsistency  
- Failure to track user-defined assumptions  

---

## Summary

These examples illustrate a consistent pattern:

> AI systems can produce locally plausible responses that are globally inconsistent.

Addressing these failure modes requires:

- explicit tracking of claims and assumptions  
- detection of contradictions  
- structured conflict resolution  

These examples motivate the constraints and metrics defined in this repository.
