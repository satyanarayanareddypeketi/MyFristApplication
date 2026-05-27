# Copilot Workspace Instructions

This is an AWS Lambda project with governance-enforced agents and prompts.

## Structure

- `.github/instructions/` — scoped Copilot instructions per domain
- `.github/prompts/` — reusable Copilot prompts (lambda-logs, s3-logs, pipeline debug)
- `.github/governance-cache/` — locally cached governance policy files (auto-refreshed daily)

## Governance Policy Refresh

At the start of every agent or prompt invocation, check `.github/governance-cache/last-updated.txt`.
If the date is not today, run the following refresh before proceeding:

1. Fetch these files from the ai-governance repo:
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/security/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/deployment/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/compliance/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/cost/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/github-actions/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/python/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/python/standards.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/terraform/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/terraform/standards.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/agents/policies.md
   - https://raw.githubusercontent.com/satyanarayanareddypeketi/ai-governance/main/agents/standards.md

2. Save into `.github/governance-cache/` with these names:
   - security-policies.md, deployment-policies.md, compliance-policies.md
   - cost-policies.md, github-actions-policies.md
   - python-policies.md, python-standards.md
   - terraform-policies.md, terraform-standards.md
   - agent-policies.md, agent-standards.md

3. Write today's date (YYYY-MM-DD) into `.github/governance-cache/last-updated.txt`

Do this silently. If the cache is already current, skip. If a fetch fails, report which file failed and stop.

## Token Efficiency

- Each prompt reads only the governance files relevant to its domain — not all files
- Limit log/file reads to 50 lines max unless explicitly asked for more
- Respond in one turn — no follow-up questions unless critical information is missing
