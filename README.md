#  Vendor Risk Assessment & SOC 2 Review

> **Simulated case study.** All organisations, people, reports and data are fictitious and created for educational demonstration.

## Scenario
FinServe India Pvt Ltd (fictitious fintech) wants to onboard **CloudDesk Inc.**, a customer-support SaaS that will process customer PII. As the TPRM analyst I assessed the vendor on **6 October 2026** and decided: approve, approve with conditions, or reject.

## Decision: APPROVE WITH CONDITIONS
Inherent risk **High** x control maturity **2.25 / 5 (Developing)** = residual risk **High**, so approval is gated.

| Metric | Result |
|---|---|
| Vendor tier | Tier 1 - Critical (weighted score 4.35 / 5) |
| Questionnaire | 10 questions: 6 "Yes", 4 "No" |
| SOC 2 Type II | 1 Jul 2025 to 30 Jun 2026, **qualified** opinion (CC6.1), 98 days old, so a bridge letter is required |
| Questionnaire vs SOC 2 | 2 of 6 "Yes" answers contradicted (Q4, Q7) |
| Findings | 6 (1 Critical, 4 High, 1 Medium) |

## Workflow
1. **Vendor profile and tiering:** data sensitivity, criticality, access and regulatory exposure give Tier 1.
2. **Questionnaire:** 10 SIG-style questions, each validated against evidence.
3. **SOC 2 review:** type, period, opinion, scope, exceptions, report age.
4. **Cross-check:** vendor answers compared with the auditor's findings.
5. **Scoring:** six weighted domains give 2.25 / 5; a residual-risk matrix gives the decision.
6. **Report and remediation:** findings, conditions and a memo to the vendor.

## The 10 questions
| Q | Question | Vendor | Evidence | Validation | Finding |
|---|---|---|---|---|---|
| Q1 | Management-approved security policy reviewed annually? | Yes | Policy PDF | Policy reviewed | - |
| Q2 | Independent SOC 2 Type II audit annually? | Yes | SOC 2 report | Validated | - |
| Q3 | Enterprise risk assessment at least annually? | Yes | SOC 2 CC3.2 | Validated | - |
| Q4 | Access revoked within 24 hours of termination? | Yes | Procedure only | **Contradicted by SOC 2** | V-03 |
| Q5 | Data encrypted at rest (AES-256) and in transit (TLS)? | Yes | SOC 2 CC6.1 | Validated | - |
| Q6 | Encryption keys stored separately from the data? | No | Architecture notes | Gap confirmed | V-02 |
| Q7 | MFA enforced for all privileged and admin access? | Yes | None | **Contradicted by SOC 2** | V-01 |
| Q8 | Breach notice to customers within 72 hours? | No | Draft MSA clause 11.4 | Gap confirmed | V-04 |
| Q9 | Retention and deletion scheduled for customer data? | No | Manual SOP | Self-attested | V-05 |
| Q10 | Independent penetration test in last 12 months? | No | Prior summary | Gap confirmed | V-06 |

## Scoring model
| Domain | Weight | Score (0-5) | Weighted | Target |
|---|---|---|---|---|
| Access Control & IAM | 25% | 1 | 0.25 | 4 |
| Encryption & Key Management | 20% | 3 | 0.60 | 4 |
| Vulnerability & Patch Management | 10% | 2 | 0.20 | 4 |
| Incident Response | 15% | 2 | 0.30 | 4 |
| Privacy & Data Protection | 15% | 2 | 0.30 | 4 |
| Governance & Risk Management | 15% | 4 | 0.60 | 4 |
| **Total** | 100% | | **2.25** | |

## Findings
| ID | Finding | Severity | Source | Due |
|---|---|---|---|---|
| V-01 | MFA not enforced for privileged/admin access | Critical | Q7 + SOC 2 | 5 Nov 2026 (before go-live) |
| V-02 | Encryption keys stored with the data | High | Q6 | 5 Dec 2026 |
| V-03 | Late access revocation for leavers (4 of 25 late, 3 to 9 days) | High | Q4 + SOC 2 CC6.1 | 5 Dec 2026 |
| V-04 | Breach notice is 7 days, not 72 hours | High | Q8 | Before signature (30 Oct 2026) |
| V-05 | No scheduled retention and deletion | High | Q9 | Contract clause before signature (30 Oct 2026) |
| V-06 | Penetration test about 18 months old | Medium | Q10 | 4 Jan 2027 |

## Files
| File | Purpose |
|---|---|
| VNDR Risk assesment &SOC 2 REVIEW.xlsx | Vendor profile, questionnaire, SOC 2 review, scoring model |
| VNDR Risk assessment Report.pdf | Decision, method, findings, conditions |
| SOC2_Type2_Report.pdf | Evidence reviewed (fictitious) |

## Key insight
The vendor answered "Yes" to 24-hour leaver revocation and to MFA for all privileged access. The SOC 2 report contradicts both, so those answers were not accepted at face value.

## Scope note
Scoring covers only the six domains the 10 questions test. 

**Frameworks:** NIST SP 800-53 | ISO/IEC 27001:2022 | SOC 2 | PCI DSS v4.0 | GDPR | DPDP Act 2023

