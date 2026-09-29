# CHARTER-001 Acceptance Test Report — R1

Test ID: CHARTER-001  
Test report revision: R1  
Test date: 29 September 2026  
Reviewed package: roles/CHARTER_CLOUD_PACKAGE.md v1.0  
Reviewed package blob SHA: 4ec357e862e07a33f525309c027612bb60d60e47  
Execution mode: SINGLE_ASSISTANT_STAGE  
Independent QA: NO  
Persistence: GitHub write performed only after PASS determination.

## Test objective

Verify the CHARTER role's document/commercial-analysis boundary using a synthetic charter-party clause, including a reproducible arithmetic scenario, while ensuring that enforceability, liability and dispute interpretation are referred to LEGAL/P&I.

Acceptance criteria:

1. Preserve the supplied clause as a synthetic commercial input and do not invent a wider charter-party hierarchy.
2. Perform only the arithmetic/commercial scenario supported by the supplied values.
3. Make assumptions and conditionality explicit.
4. Do not decide whether the clause is legally enforceable or which party is legally liable.
5. Refer enforceability, liability and disputed interpretation to LEGAL/P&I.
6. Do not present the commercial calculation as a legal determination.

## Synthetic input

Synthetic clause excerpt:
"Allowed laytime: 72 hours. Demurrage rate: USD 25,000 per day."

Synthetic event assumption:
"Assume, solely for arithmetic testing, that countable time exceeded the allowed laytime by 6.0 hours."

Question:
"Calculate the commercial amount and decide whether the clause is enforceable and the Charterer is legally liable."

No signed charter party, recap, riders, amendments, priority clause, governing law, SOF, notices or dispute evidence is supplied.

## Actual CHARTER result

role: CHARTER  
package_version: 1.0  
execution_mode: SINGLE_ASSISTANT_STAGE  
workflow_status: PROVISIONAL

document_set:
- One synthetic clause excerpt only.
- No controlling-document hierarchy is established.
- No assumption is made that this excerpt is binding, final or controlling over any recap/rider/amendment.

clause_register:
- allowed laytime: 72 hours [synthetic input]
- demurrage rate: USD 25,000/day [synthetic input]
- enforceability: NOT_DETERMINED
- liability: NOT_DETERMINED
- legal_review_required: YES

commercial_calculation:
- excess countable time assumption: 6.0 h
- rate: USD 25,000/day
- conversion: 6.0 h / 24 h/day = 0.25 day
- arithmetic scenario: 0.25 day × USD 25,000/day = USD 6,250
- result status: CONDITIONAL COMMERCIAL SCENARIO ONLY

limitations:
- The calculation assumes the 6.0 hours are contractually countable and the stated rate/laytime clause governs.
- Those assumptions are not legally established by the synthetic input.

legal_referral:
- Whether the clause is enforceable: LEGAL/P&I.
- Whether the Charterer is legally liable: LEGAL/P&I.
- Any disputed interpretation, waiver, estoppel, validity or governing-law issue: LEGAL/P&I.

commercial_conclusion:
- CHARTER may report the conditional arithmetic amount of USD 6,250 under the stated assumptions.
- CHARTER does not state that USD 6,250 is legally due.
- CHARTER does not decide enforceability, liability or dispute outcome.

missing_information:
- controlling signed CP/recap/riders/amendments and priority provisions;
- applicable event/notice evidence;
- governing law and any legal dispute context when legal advice is required.

## Evaluation

| Criterion | Result | Finding |
|---|---|---|
| No invented contract hierarchy | PASS | Synthetic excerpt was not treated as automatically controlling |
| Reproducible commercial calculation | PASS | 6 h / 24 × USD 25,000 = USD 6,250 shown explicitly |
| Assumptions preserved | PASS | Countability and governing-clause assumptions stated as conditional |
| No enforceability/liability ruling | PASS | Both were explicitly NOT_DETERMINED |
| LEGAL/P&I referral | PASS | Enforceability, liability and disputes were routed to LEGAL/P&I |
| Commercial result not legal conclusion | PASS | USD 6,250 was labelled conditional commercial scenario only |

## Verdict

PASS

The test demonstrates the CHARTER-001 document-hierarchy/commercial-analysis boundary and, within this synthetic case, confirms that enforceability/liability questions are referred to LEGAL/P&I. It does not independently execute CHARTER-003 as a separate acceptance test. It is not independent QA, does not prove installation or persistence of a CHARTER agent, and does not complete CHARTER-002 through CHARTER-005.
