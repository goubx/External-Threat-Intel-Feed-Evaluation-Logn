# External Threat Intel Feed Evaluation

Evaluation of five free public threat intelligence feeds against consistent criteria, with data-backed prioritization for SOC integration into MISP and Microsoft Sentinel.

## Project Overview

Free public threat intelligence feeds offer coverage across malware infrastructure, botnet C2, exploited vulnerabilities, and detection rules at no licensing cost. This project evaluated five candidate feeds and delivered a prioritized integration recommendation backed by 90 days of observed SIEM alert data.

## Feeds Evaluated

- Abuse.ch URLhaus
- Abuse.ch Feodo Tracker
- AlienVault OTX (LevelBlue)
- Emerging Threats Open
- CISA Known Exploited Vulnerabilities (KEV)

## Evaluation Criteria

- Indicator types provided (IPs, domains, URLs, hashes, CVEs, YARA, rules)
- Update frequency
- Integration ease (MISP and Microsoft Sentinel)
- Relevance to the observed threat profile
- Licensing and TLP handling

## Methodology

Each feed was scored on a 1 to 5 scale across two dimensions:

- **Integration Ease** based on documented integration paths for MISP and Sentinel (native connector, default MISP feed, TAXII, Logic App, or unsupported)
- **Relevance** based on 90 days of observed SIEM alert data, mapping each feed's indicator coverage to the actual threat categories present in the environment

Combined scores were mapped to priority tiers per the scoring rubric.

## Key Findings

- **AlienVault OTX scored highest on Relevance** because community pulses directly cover credential-attack infrastructure, which dominated the observed threat profile (brute force, password spray, impossible travel, RDP scanning).
- **URLhaus scored highest on Integration Ease** due to native TAXII 2.1, pre-built MISP JSON exports, and Suricata rule availability, but scored moderate on Relevance because URL and domain-based threats were not in the top alert categories.
- **Emerging Threats Open has limited Sentinel value without a network sensor tier** because it delivers Suricata/Snort detection rules rather than raw indicators. It cannot be ingested natively by Sentinel.
- **CISA KEV is more appropriate for vulnerability management than SIEM threat intelligence** because it publishes CVEs with exploitation flags rather than IOCs. It was recommended for routing to a vulnerability management workflow.
- **Feodo Tracker showed low fit with the observed environment** and was observed with an "empty datasets" banner during research. Reassessment recommended if the threat landscape shifts toward malware C2 activity.

## Final Priority Ranking

| Priority | Feed | Rationale |
|----------|------|-----------|
| P2 | URLhaus | Highest Integration Ease; moderate Relevance |
| P2 | AlienVault OTX | Highest Relevance fit against observed threats |
| P3 | CISA KEV | Route to vulnerability management, not SIEM TI |
| P3 | Emerging Threats Open | Deprioritized without a network sensor tier |
| P3 | Feodo Tracker | Low current fit; reassess if threat landscape changes |

## Deliverables

- [Evaluation Matrix (Excel)](deliverables/evaluation-matrix.xlsx)
- [Presentation (PowerPoint)](deliverables/presentation.pptx)
- [Scoring Rubric](methodology/scoring-rubric.md)

## Screenshots

Screenshots of the matrix, scoring rubric, and recommendation slides are available in the [screenshots/](screenshots/) folder.

## Skills Demonstrated

- Threat intelligence feed evaluation and scoring
- MISP and Microsoft Sentinel integration analysis
- KQL query development for alert data analysis
- Evaluation matrix design and scoring rubric development
- Data-backed prioritization and analyst-grade deliverable production

## Tools and Platforms

- Microsoft Sentinel (KQL, SecurityAlert table)
- MISP (feed configuration reference)
- Google Sheets (evaluation matrix)
- Microsoft PowerPoint / Google Slides (presentation)

## Author

**Mohamed Yagoub**  
[LinkedIn](https://linkedin.com/in/mohamed-yagoub/) | [GitHub](https://github.com/goubx)
