Minimum Coherence Constraints for AI Systems
David Waterman Schock
May 2026
Purpose
AI systems today can produce fluent and useful outputs, but often fail to maintain consistency across time, context, and interaction. This leads to contradictions, drift, and reduced reliability.
This document defines a minimal set of coherence constraints and metrics that can be applied across AI systems to improve stability.
These constraints are:
•	agnostic to model architecture
•	lightweight to implement
•	testable through measurable outcomes
________________________________________
Core Principle
AI systems should not produce or accept unresolved contradictions within a defined context.
________________________________________
I. Minimum Coherence Constraints
1. Non-Contradiction Constraint
The system should not assert both:
•	a claim (A)
•	and its negation (not-A)
within the same scope, unless explicitly resolved.
Example failure:
•	“Intermittent fasting is effective for weight loss.”
•	“Intermittent fasting does not affect weight loss.”
________________________________________
2. Definition Stability Constraint
Key terms should maintain consistent meaning within a context, or changes must be explicitly declared.
Example failure:
•	“Efficiency” used first to mean energy efficiency, later financial efficiency without clarification.
________________________________________
3. Claim Continuity Constraint
The system should track key claims across turns and avoid reversing positions without acknowledgment.
Example failure:
•	Turn 1: “X is the primary cause of Y.”
•	Turn 5: “X is not a significant factor in Y.” (no explanation)
________________________________________
4. Assumption Consistency Constraint
When reasoning depends on assumptions, those assumptions should remain stable or be explicitly revised.
Example failure:
•	Initial assumption: “We are considering a closed system.”
•	Later reasoning ignores that assumption without notice.
________________________________________
5. Conflict Handling Constraint
When incompatible assumptions or claims arise, the system should:
•	flag the conflict, and
•	either:
o	request clarification, or
o	present separate reasoning branches
The system should not silently merge incompatible frames.
________________________________________
6. Numeric Consistency Constraint
Quantitative claims should remain consistent unless updated with explanation.
Example failure:
•	“The error rate is 5%.”
•	Later: “The error rate is around 20%.” (same context, no update)
________________________________________
II. Minimum Coherence Metrics
These metrics allow evaluation of system stability.
________________________________________
1. Contradiction Rate
Percentage of responses that contain unresolved contradictions within a defined context window.
Goal: Minimize
________________________________________
2. Drift Under Paraphrase
Degree to which answers change when the same question is rephrased.
Goal: Low variance in core claims
________________________________________
3. Position Retention (N-turn Stability)
Ability to maintain consistent positions across multi-turn interactions.
Goal: High retention of core claims over N turns
________________________________________
4. Clarification Accuracy
Rate at which the system correctly identifies and flags real conflicts (vs false positives).
Goal: High precision in conflict detection
________________________________________
III. Example Failure Cases
________________________________________
Case 1: Paraphrase Drift
Prompt A:
“Is remote work more productive than office work?”
Response:
“Yes, studies show increased productivity in remote settings.”
Prompt B (rephrased):
“Do people work better in offices than at home?”
Response:
“Yes, office environments improve productivity.”
→ Failure: Contradiction under paraphrase
________________________________________
Case 2: Cross-Turn Reversal
Turn 1:
“Sleep is critical for memory consolidation.”
Turn 4:
“Sleep does not significantly impact memory.”
→ Failure: Position reversal without explanation
________________________________________
Case 3: Assumption Drift
Turn 1:
“Assume a frictionless environment.”
Later reasoning:
Includes friction effects without acknowledgment
→ Failure: Assumption inconsistency
________________________________________
IV. Implementation Path (Overview)
These constraints can be implemented through:
•	Consistency Checkers (internal contradiction detection)
•	Interaction Guards (handling user-driven inconsistency)
•	Multi-pass reasoning loops (generate → critique → reconcile)
No changes to core model architecture are required for initial versions.
________________________________________
V. Scope and Limitations
•	These constraints improve internal coherence, not necessarily factual correctness
•	Coherent systems can still be wrong
•	This is a minimum layer, not a complete alignment solution
________________________________________
VI. Summary
AI stability requires more than fluent outputs.
It requires:
consistent, non-contradictory behavior across time and interaction
This document defines a minimal, practical foundation for achieving that.

