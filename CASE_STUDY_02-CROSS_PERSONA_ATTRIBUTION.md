
# Case Study 02: Cross-Persona Threat Attribution via Psycholinguistic & Operational Tempo Analysis

Classification: Sanitized Methodology Demonstration | Domain: Behavioral Threat Attribution, OSINT & Linguistic Forensics
Tools Utilized: Obsidian, Maltego, Wireshark, Custom Python Stylometry Scripts

## 1. Executive Scenario

A cross-border financial advisory firm suffered a targeted executive impersonation and fraudulent wire redirection attempt. Standard network forensics hit a technical dead end after investigators found the lookalike domain was registered behind a privacy proxy, routed through rotating burner infrastructure, and tied to decentralized cryptocurrency swaps.

## 2. Four-Pillar Attribution & Triage

### A. Psycholinguistic & Syntactic Fingerprinting (Pillar 1)
* **Idiolect Extraction:** Analyzed punctuation anomalies, non-standard prepositional phrasing, and recurring lexical markers across the adversary's pretext emails and follow-up extortion messages.
* **Stress-Escalation Profiling:** Documented a consistent shift from formal corporate mimicry to aggressive, abbreviated syntax whenever target compliance was delayed.

### B. Operational Tempo & Circadian Mapping (Pillar 2)
* **Activity Window Modeling:** Correlated SMTP header timestamps, domain DNS modifications, and on-chain swap executions over a 14-day window.
* **Timezone & Routine Isolation:** Identified a strict daily dormancy period between 02:00 and 07:30 UTC, narrowing the actor's probable primary operating window to UTC+2 / UTC+3.

### C. Victimology & Cross-Persona OSINT Correlation (Pillars 3 & 4)
* **Pretext Engineering Review:** Evaluated the adversary's familiarity with internal board approval workflows, indicating prolonged passive reconnaissance prior to outreach.
* **Cross-Platform Pivot:** Queried unique syntactic strings and rare spelling quirks across breached forum datasets and public OSINT repositories, linking the burner email persona to an established threat actor handle active on underground infrastructure marketplaces.

## 3. Attribution Synthesis & Operational Takeaways

* **High-Confidence Behavioral Linkage:** Although network indicators were completely obfuscated, the convergence of idiolect markers, circadian dormancy windows, and pretext structure established high-confidence attribution across separate threat personas.
* **Defensive Recommendations:** Implemented domain-spoofing monitoring, out-of-band executive wire verification protocols, and behavioral threat intelligence tracking for recurring adversary personas
