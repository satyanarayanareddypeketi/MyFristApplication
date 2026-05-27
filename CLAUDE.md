# CLAUDE.md

This file is automatically read by Claude Code when you open this project.

## Project Overview
This repo was scaffolded by DevPipeline Studio with a GitHub Actions CI/CD pipeline,
Lambda function code, Terraform infrastructure, and AI-powered agents and skills.

## Active Agents
Agents are located in `.claude/agents/`. Each agent has a specific role in the pipeline.

### CodeGuardian
- File: `.claude/agents/CodeGuardian.md`
- Read this file to understand the agent's purpose and instructions.

### DeployAssure
- File: `.claude/agents/DeployAssure.md`
- Read this file to understand the agent's purpose and instructions.


## Available Skills
Skills are located in `.claude/commands/`. Each skill is a slash command you can invoke in Claude Code.

### LambdaLogFetch
- File: `.claude/commands/lambda-logs-fetch.md`
- Use as a slash command: `/lambdalogfetch`


## Project Structure
```
.claude/
  agents/        # AI agent instruction files
  commands/      # Claude Code slash commands (skills)
.github/
  workflows/     # GitHub Actions CI/CD pipeline
terraform/       # Infrastructure as code
tests/           # Unit tests
lambda_function.py  # AWS Lambda handler
```

## Pipeline Stages
1. Build
2. Unit Test
3. Security Scan
4. Package
5. Deploy
