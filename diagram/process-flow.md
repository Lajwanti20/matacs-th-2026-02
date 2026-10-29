
# AI Proposal Triage — Process Flow

```mermaid
flowchart TD
    A[Upload Contractor Proposal] --> B[AI Extracts Proposal Information]
    B --> C[Validate Extracted Fields and Source Evidence]
    C --> D{Missing or Suspicious Information?}
    D -- Yes --> E[Flag for Human Review]
    D -- No --> F[Apply Deterministic Rules]
    E --> F
    F --> G{Mandatory Requirements Passed?}
    G -- No --> H[Mark Ineligible]
    G -- Yes --> I[Apply Configured Weighted Scoring]
    I --> J[Generate Scores, Ranking and Reasons]
    H --> K[Human Reviewer Checks Results]
    J --> K
    K --> L{Reviewer Accepts Results?}
    L -- No --> M[Correct Evidence or Record Override]
    M --> K
    L -- Yes --> N[Record Final Decision and Audit Log]
    N --> O[Human Makes Final Award Decision]
```

## Process Description

1. **Upload:** The contractor proposal enters the system.
2. **AI extraction:** AI extracts relevant experience, licence, insurance, price, timeline, warranty, and team information.
3. **Validation:** Extracted values are checked against source evidence. Missing information and suspicious instructions are flagged.
4. **Rule-based evaluation:** Deterministic code checks mandatory eligibility requirements and applies administrator-configured weighted scoring.
5. **Results:** The system produces scores, rankings, reasons, and flags.
6. **Human review:** A reviewer checks the evidence, resolves uncertainty, and records any corrections or overrides.
7. **Final decision:** The human makes the award decision, and the system retains an audit trail.
