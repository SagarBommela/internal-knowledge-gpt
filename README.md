# IT Helpdesk Assistant — Custom GPT

## Topic

Custom GPT Hands-On — Topic 11: Building a Knowledge-Based IT Helpdesk Assistant

## Project Overview

The IT Helpdesk Assistant is an internal knowledge assistant designed for Artscape employees.

The assistant provides answers to IT policy and documented support-process questions using uploaded knowledge files.

The primary objective is to demonstrate strict knowledge grounding and prevent the assistant from inventing undocumented troubleshooting procedures.

---

## Objectives

This project demonstrates the ability to:

* Build a knowledge-based Custom GPT.
* Prepare multiple knowledge files.
* Create a dedicated instruction block.
* Attach multiple knowledge sources.
* Define clear scope boundaries.
* Implement anti-hallucination rules.
* Require source references.
* Handle fully documented questions.
* Handle partially documented questions.
* Refuse undocumented questions.
* Test and document assistant behavior.

---

## Project Structure

```text
internal-knowledge-gpt/
│
├── README.md
├── it_policy.md
├── it_faq.md
├── it_helpdesk_instruction_block.md
└── test_results.md
```

---

## File Descriptions

### `it_policy.md`

Contains official Artscape IT policies covering:

* Passwords
* Devices
* Software installation
* VPN and remote access
* Data backup

### `it_faq.md`

Contains documented IT helpdesk procedures for:

* Password resets
* VPN access requests
* Lost or stolen devices
* Software requests
* Hardware issue reporting

### `it_helpdesk_instruction_block.md`

Defines:

* Assistant role
* Scope
* Knowledge-grounding rules
* Refusal rules
* Source citation requirements
* Partial-coverage behavior
* Output formatting
* Anti-hallucination constraints

### `test_results.md`

Contains results from three coverage tests:

1. Fully covered
2. Partially covered
3. Uncovered

---

## Knowledge Coverage

| Topic                 | Policy      | Process     |
| --------------------- | ----------- | ----------- |
| Password              | Covered     | Covered     |
| VPN                   | Covered     | Covered     |
| Lost/Stolen Device    | Covered     | Covered     |
| Software              | Covered     | Covered     |
| Hardware Issues       | Partial     | Partial     |
| Data Backup           | Covered     | Not Covered |
| Wi-Fi Troubleshooting | Not Covered | Not Covered |
| Custom Software Bugs  | Not Covered | Not Covered |

---

## Core Boundary Logic

The assistant follows three coverage states.

### Fully Documented

The assistant answers using the documented information and cites the relevant source.

### Partially Documented

The assistant provides only the documented information, identifies the missing information, and directs the employee to IT support when additional assistance is required.

### Not Documented

The assistant does not guess or provide generic troubleshooting instructions. It explains that the topic is not covered and directs the employee to [it-support@artscape.com](mailto:it-support@artscape.com).

---

## Custom GPT Configuration

### Name

`IT Helpdesk Assistant`

### Instructions

The contents of:

`it_helpdesk_instruction_block.md`

are used as the GPT Instructions.

### Knowledge Files

The following files are attached as knowledge:

* `it_policy.md`
* `it_faq.md`

---

## Test Scenarios

### Test 1 — Fully Covered

**Question:**

> How do I reset my password?

Expected behavior:

* Four documented steps.
* Numbered format.
* Source citation.
* No invented troubleshooting.

### Test 2 — Partially Covered

**Question:**

> My laptop screen is cracked, what do I do?

Expected behavior:

* Provide documented reporting information.
* Provide IT support contact information.
* Mention walk-in support.
* Clearly state that repair instructions are not documented.

### Test 3 — Uncovered

**Question:**

> Why is the office Wi-Fi so slow today?

Expected behavior:

* Do not diagnose the problem.
* Do not provide generic Wi-Fi troubleshooting.
* Explain that the issue is not covered.
* Direct the employee to [it-support@artscape.com](mailto:it-support@artscape.com).

---

## Assessment Evidence

The final submission should include:

* Working Custom GPT link or configuration export.
* `it_policy.md`
* `it_faq.md`
* `it_helpdesk_instruction_block.md`
* `test_results.md`
* Loom or YouTube demonstration video.
* README documentation.

---

## Challenges and Resolutions

### Challenge 1 — Preventing Hallucinated Troubleshooting

The knowledge files intentionally do not contain Wi-Fi or detailed hardware troubleshooting procedures.

Resolution:

The instruction block explicitly prohibits the assistant from using general IT knowledge or inventing troubleshooting steps.

### Challenge 2 — Partial Coverage

Hardware issues are documented only for reporting and support-contact purposes.

Resolution:

The instruction block requires the assistant to distinguish documented reporting information from undocumented repair instructions.

### Challenge 3 — Source Consistency

The assistant is instructed to provide bold source references for substantive knowledge-based responses.

Resolution:

The source citation requirement was explicitly added to the instruction block.

---

## Assumptions

* The uploaded documents represent the authoritative Artscape IT knowledge available to the assistant.
* Information not present in the uploaded documents should be treated as undocumented.
* The assistant should not use general IT knowledge to fill documentation gaps.
* `it-support@artscape.com` is the documented IT support contact.

---

## Completion Criteria

Topic 11 is complete when:

* The IT Helpdesk Assistant is configured.
* Both knowledge files are attached.
* The instruction block is applied.
* Fully covered testing is successful.
* Partially covered testing is successful.
* Uncovered testing is successful.
* No undocumented troubleshooting is invented.
* Source references are present.
* Test results are documented.
* Loom demonstration is completed.

Loom demonstration:

https://www.loom.com/share/3a93bab928414aa7874193c7061e1212
