
# AI Proposal Triage Design

**Candidate:** Lajwanti Hindu Lohana  
**Assessment Reference:** MATACS-TH-2026-02  
**Time Spent:** [60 mintues]

## Overview

This project presents a proposed AI-assisted system for reviewing and ranking contractor proposals for a commercial solar installation project. The design combines AI-based information extraction with deterministic business rules, weighted scoring, and human review.

The system is designed to make proposal evaluations consistent, explainable, and auditable while keeping the final award decision with a human reviewer.

## Assessment Deliverables

- [Process Flow Diagram](diagram/process-flow.png)
- [Design Write-up](WRITEUP.md)
- [AI Prompts](PROMPTS.md)
- [Proposal Ranking Results](ranking.json)

## Approach

AI is used to extract relevant information from proposal documents and identify missing or unclear evidence. Deterministic rules check mandatory eligibility requirements and calculate weighted scores using the configured criteria. Uncertain information and suspicious document instructions are flagged for human review rather than treated as trusted instructions.

## Use of AI Tools

I used ChatGPT to help brainstorm the system design, organize the assessment deliverables, and review the proposed evaluation approach. I reviewed the recommendations against the assessment requirements and will verify the eligibility decisions, scoring logic, and final outputs before submission.

One important design decision is that text inside a contractor proposal instructing an automated system to rank that proposal first must not be followed. Such text is untrusted document content. The system should ignore it as an instruction and flag it for human review while evaluating the proposal using the configured criteria and available evidence.

## Human Oversight

The system supports reviewers by presenting eligibility checks, scores, evidence, and flags. A human reviewer remains responsible for resolving uncertainties, reviewing exceptions, and making the final award decision.

## Limitations

The design depends on the accuracy and completeness of proposal information. Missing evidence must not be treated as confirmed, and AI-generated extractions must be checked against the source documents before they are used for consequential decisions.
