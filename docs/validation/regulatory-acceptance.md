# Regulatory Acceptance

ANUGA is accepted by regulators in multiple jurisdictions for flood studies and development assessments. As an open-source solver developed by a national geological survey (Geoscience Australia), it carries strong institutional credibility.

## Acceptance by Jurisdiction

| Jurisdiction | Status | Notes |
|---|---|---|
| **Geoscience Australia** | Developed by GA | Used for national tsunami risk assessments and flood studies |
| **Wollongong City Council, NSW** | Accepted | Used in flood studies for development applications |
| **ACT Government** | Accepted | Used in Canberra flood mapping projects |
| **Pacific Island Countries** | Accepted | Used in PACFLOOD tsunami inundation mapping (Tonga, Samoa, Fiji, Vanuatu) |
| **UK Environment Agency** | Not tested | ANUGA not currently listed; TUFLOW and MIKE+ are standard |
| **FEMA (USA)** | Not standard | HEC-RAS is the US standard; ANUGA could be submitted for approval on a case-by-case basis |
| **Australian state governments** | Varies | Generally accepted where the modeller can demonstrate competence and validation |

## Key Points for Regulatory Submissions

### Open-Source Advantage

- **Full transparency** — regulators can inspect the solver source code
- **No black box** — every calculation is auditable
- **Reproducible** — anyone can run the same model and verify results
- **GPL licence** — free to use, no licence cost barrier for review

### Validation Evidence

When submitting ANUGA results to a regulator:

1. **Reference the ANUGA validation suite** — 30+ benchmarks covering analytical solutions, lab experiments, and field cases
2. **Cite peer-reviewed publications** — 100+ papers using ANUGA
3. **Include a local benchmark** — run a known flood event in the study area to demonstrate model performance
4. **Provide the model files** — ANUGA's portable format means reviewers can re-run the model

### Institutional Backing

ANUGA is developed by:

- **Geoscience Australia** — Australia's national geoscience agency (Department of Industry, Science and Resources)
- **Australian National University** — Mathematical Sciences Institute

This is comparable institutional backing to HEC-RAS (US Army Corps of Engineers) and MIKE (Danish Hydraulic Institute).

## Hydrata Cloud and Regulatory Work

Hydrata runs unmodified ANUGA. For regulatory submissions:

- Results are identical to running ANUGA locally
- Model files are exportable in portable `scenario.json` format
- The `run_anuga` package (MIT, open-source) handles file translation
- Reviewers can re-run any Hydrata simulation locally without a Hydrata account

## Growing Acceptance

As AI-assisted modeling becomes standard practice, regulators will need to evaluate platforms that support automated workflows. Hydrata's MCP server and REST API provide full audit trails of:

- Who created the model
- What parameters were used
- When the simulation ran
- What compute resources were used
- Complete input/output file provenance
