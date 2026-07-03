# Scoring Rubric

## Integration Ease Score (1 to 5)

| Score | Meaning |
|-------|---------|
| 5 | Native connector or default MISP feed on both platforms. Enable in UI, no code required. |
| 4 | Pre-built export in standard format (TAXII, MISP JSON, STIX). Documented, minor config. |
| 3 | Documented API pull. Requires Logic App, script, or scheduled job to fetch and transform. |
| 2 | Custom parser needed. Non-standard format, requires engineering effort. |
| 1 | Not natively supported on target platform. Significant conversion or workaround required. |

Score reflects the harder of MISP or Sentinel integration, the weakest link.

## Relevance Score (1 to 5)

| Score | Meaning |
|-------|---------|
| 5 | Directly maps to multiple current threats observed in the environment. |
| 4 | Covers threats regularly seen in the environment or high-value context. |
| 3 | Covers threats occasionally seen, or provides useful enrichment. |
| 2 | Tangentially relevant, limited overlap with observed threats. |
| 1 | Not aligned with the current threat profile. |

Relevance was scored against 90 days of SIEM alert data.

## Overall Priority

Combined score (Integration Ease + Relevance) maps to a priority tier.

| Combined Score | Priority Tier |
|---------------|---------------|
| 9-10 | Priority 1 - Integrate immediately |
| 7-8 | Priority 2 - Integrate in next sprint |
| 5-6 | Priority 3 - Integrate when capacity allows |
| 3-4 | Priority 4 - Deprioritize, revisit later |
| 2 | Do not integrate |

## KQL Queries Used

Query 1: Top SecurityAlert categories over 90 days
