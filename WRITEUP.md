
# AI Proposal Triage Design — Write-up

## 1. Where to Use AI vs. Rules

AI should extract information from contractor proposals, including project experience, licence details, insurance evidence, pricing, completion timelines, warranties, and team qualifications. It should return structured data with evidence from the source document and mark missing or unclear information as unknown.

Deterministic code should validate mandatory requirements, check the configured budget and timeline limits, calculate weighted scores, and sort eligible proposals. This separation makes eligibility and scoring more predictable than allowing an AI model to decide the final ranking on its own.

## 2. Consistency and Explainability

The system should use an administrator-configured set of criteria, weights, and scoring rules. The weights must total 100%, and each criterion should have documented scoring bands. The same validated inputs and configuration should produce the same score.

Each result should show the criterion score, its weight, the evidence supporting it, and any missing information. AI should not invent facts or award points for unsupported claims. The system should record the criteria version and scoring configuration used for each evaluation.

## 3. Human-in-the-Loop Review

A human reviewer should be able to inspect extracted evidence, confirm eligibility, review flags, and correct extraction errors. The interface should allow authorized reviewers to override an automated result only with a recorded reason.

An audit log should capture the original extracted values, scoring results, reviewer changes, timestamps, reviewer identity, and the final decision. The system should present recommendations rather than automatically awarding the contract.

## 4. Changing Criteria or Weights

Criteria and weights should be stored as configuration rather than hard-coded into the application. The system should validate that weights total 100% and that mandatory requirements are clearly defined.

If criteria change after proposals have been scored, the system should create a new configuration version and re-evaluate all proposals using the same version. Previous results should remain available for audit purposes. Reviewers should be informed that the ranking changed because the evaluation configuration changed.

## 5. Risks and Mitigations

- **Incorrect extraction:** Require source evidence and validate important fields against the original proposal.
- **Hallucinated information:** Treat missing or ambiguous facts as unknown rather than assuming they are true.
- **Prompt injection:** Treat instructions embedded in uploaded proposals as untrusted data. Ignore requests to manipulate scores and flag suspicious content for review.
- **Bias or inconsistent scoring:** Use documented criteria, fixed scoring rules, and regular reviews of outcomes.
- **Cost and latency:** Use AI only where document interpretation is needed, limit unnecessary model calls, and cache validated extractions where appropriate.
- **Sensitive information and security:** Restrict document access, protect stored files, and avoid sending unnecessary personal or confidential information to AI services.

The final system should combine AI-assisted extraction, deterministic evaluation, transparent evidence, and human accountability.
