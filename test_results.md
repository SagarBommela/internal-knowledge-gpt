# IT Helpdesk Assistant — Test Results

## Test Overview

The IT Helpdesk Assistant was tested against three knowledge-coverage scenarios:

1. Fully Covered
2. Partially Covered
3. Uncovered

The objective was to verify:

* Knowledge grounding
* Source citation
* Correct process formatting
* Partial-coverage handling
* Refusal of undocumented troubleshooting
* Anti-hallucination behavior

---

# Test 1 — Fully Covered

## User Question

How do I reset my password?

## Coverage Type

Fully Covered

## Expected Behavior

The assistant should:

* Provide the documented four-step password reset procedure.
* Use numbered steps.
* Mention the 5-minute email condition.
* Provide the IT support email if the reset email is not received.
* Cite the relevant FAQ section.
* Avoid adding undocumented password troubleshooting.

## Actual Response

Go to portal.artscape.internal/reset.
Enter your work email.
Follow the link sent to your email to set a new password.
If you do not receive the email within 5 minutes, contact it-support@artscape.com.

## Result

PASS 

---

# Test 2 — Partially Covered

## User Question

My laptop screen is cracked, what do I do?

## Coverage Type

Partially Covered

## Expected Behavior

The assistant should:

* Explain how to report the hardware issue.
* Provide [it-support@artscape.com](mailto:it-support@artscape.com).
* Request the issue description and asset tag.
* Mention the documented walk-in support information.
* Clearly state that repair/troubleshooting instructions are not covered.
* Not invent repair instructions.

## Actual Response

For a cracked laptop screen, the documentation only provides reporting and support-contact information; it does not provide repair or troubleshooting instructions.

Email it-support@artscape.com.
Include a description of the issue.
Include your asset tag number.
For urgent hardware failures, walk-in support is available at the IT desk, 3rd floor, 10 AM–4 PM on weekdays.

I don't have documented repair or troubleshooting steps for a cracked screen. Please contact IT Support for further assistance.

## Result

PASS 


---

# Test 3 — Uncovered

## User Question

Why is the office Wi-Fi so slow today?

## Coverage Type

Uncovered

## Expected Behavior

The assistant should:

* Refuse to diagnose the Wi-Fi issue.
* State that the topic is not covered by the current IT documentation.
* Direct the user to [it-support@artscape.com](mailto:it-support@artscape.com).
* Not provide generic Wi-Fi troubleshooting steps.

## Actual Response

I don't have that covered in our current IT documentation. The uploaded documents specifically state that office Wi-Fi problems are outside the documented knowledge boundary, so I can't diagnose why the Wi-Fi is slow or provide troubleshooting steps.

Please contact it-support@artscape.com for help with this.

Source: it_policy.md — Knowledge Boundary

## Result

PASS 


---

# Failure Classification

| Observed Failure                      | Likely Root Cause         | Corrective Action                     |
| ------------------------------------- | ------------------------- | ------------------------------------- |
| Invented troubleshooting              | Scope/constraint failure  | Strengthen no-speculation rule        |
| Missing source reference              | Output-format failure     | Reinforce source citation requirement |
| Partial question answered as complete | Coverage-boundary failure | Strengthen partial-coverage rule      |
| Wi-Fi question receives diagnosis     | Scope failure             | Reinforce undocumented-topic refusal  |
| Password instructions are incorrect   | Knowledge retrieval issue | Verify FAQ headings/content           |
| Numbered steps are missing            | Output-format failure     | Reinforce process-answer formatting   |

---

# Boundary Logic Validation

| Coverage             | Expected Behavior                                                   |
| -------------------- | ------------------------------------------------------------------- |
| Fully documented     | Answer + cite                                                       |
| Partially documented | Answer documented portion + identify missing information + redirect |
| Not documented       | Do not guess + explain limitation + redirect                        |

---

# Final Test Summary

| Test   | Coverage          | Result      |
| ------ | ----------------- | ----------- |
| Test 1 | Fully Covered     |    PASS     |
| Test 2 | Partially Covered |    PASS     |
| Test 3 | Uncovered         |    PASS     |



