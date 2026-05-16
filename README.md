# Build a Completely Free OpenClaw AI Agent on Linux with Ollama + Telegram

A practical field guide for building a local AI agent stack on Linux using OpenClaw, Ollama, Telegram and workflow automation.

This guide is based on real deployment work, debugging, failures, validation and security checks.

It is not a theoretical tutorial.

## Goal

Build a local AI agent capable of operating as a task executor, not only as a chatbot.

The system was designed to:

- run locally
- use free or local components
- avoid paid APIs as a requirement
- connect OpenClaw with local and external model providers
- integrate with Telegram
- support workflow automation
- validate every step from terminal
- avoid exposing credentials or sensitive endpoints

## Tested environment

Operating System: Linux Mint

GPU: NVIDIA GTX 1650

VRAM: 4 GB

Runtime: local workstation

Main local runtime: Ollama

Agent framework: OpenClaw

Automation layer: n8n

Messaging layer: Telegram

Execution mode: local-first

## Architecture

The system was separated into components:

Linux Mint

↓

OpenClaw

↓

OpenClaw Gateway

↓

Model provider layer

↓

Ollama / external providers

↓

Local or remote model

↓

Skills

↓

n8n workflows

↓

Telegram interface

## Important clarification

OpenClaw is not the model.

OpenClaw coordinates the agent behavior.

The model provider performs inference.

Ollama can expose local models.

External providers can also be configured.

The agent brain depends on the active provider and model configuration.

## Model experimentation

The deployment did not rely on a single model from the beginning.

Real experiments included:

- Ollama + Qwen2 1.5B
- Ollama + Qwen2.5 3B
- Moonshot Kimi K2.5
- Moonshot Kimi K2.6
- NVIDIA Nemotron models
- OpenAI-compatible provider configurations

The goal was not to use the largest model.

The goal was to find a stable configuration for the available hardware.

## Hardware limitations

The GTX 1650 with 4 GB VRAM was a major constraint.

Observed behavior:

- large models caused instability
- some models loaded but responded slowly
- VRAM became a constant limitation
- local video generation was not realistic on this hardware
- smaller models were more operationally useful
- model selection required real testing, not only benchmarks

Lesson:

A smaller stable model is better than a larger unstable model.

## Deployment journey

The real process was not linear.

Stages included:

1. Linux Mint preparation
2. Node installation with NVM
3. OpenClaw installation
4. OpenClaw version updates
5. Gateway configuration
6. Ollama setup
7. Local model testing
8. Provider testing
9. OpenClaw configuration inspection
10. Skills discovery
11. Telegram integration
12. n8n validation
13. Service debugging
14. Security scanning
15. GitHub publication

## OpenClaw internal investigation

Important local areas inspected:

- ~/.openclaw
- openclaw.json
- completions
- logs
- sessions
- providers
- skills
- systemd user services

Useful commands:

openclaw skills check

openclaw skills list

openclaw skills info github

find ~/.openclaw -type f

grep -R "provider\|model" ~/.openclaw

systemctl --user status openclaw-gateway

## Validation commands

The system was validated from terminal.

Examples:

systemctl --user status openclaw

systemctl --user status openclaw-gateway

systemctl --user status ollama

ss -tulpn | grep <OLLAMA_PORT>

ss -tulpn | grep <AUTOMATION_PORT>

curl http://localhost:<OLLAMA_PORT>/api/tags

curl http://localhost:<LOCAL_AGENT_PORT>/health

ollama list

openclaw skills check

## Telegram integration

Telegram was used as an external interaction channel.

The guide intentionally avoids publishing:

- bot token
- bot username
- webhook URL
- private chat IDs
- production endpoints

Only the integration concept is documented.

## Security rules

Do not publish:

- API keys
- tokens
- passwords
- bot credentials
- private endpoints
- personal ports
- internal usernames
- LAN IP addresses
- webhook URLs
- .env files
- raw config files with secrets

Use placeholders instead:

- <OLLAMA_PORT>
- <OPENCLAW_GATEWAY_PORT>
- <LOCAL_AGENT_PORT>
- <AUTOMATION_PORT>
- <TELEGRAM_BOT_TOKEN>
- <WEBHOOK_URL>

## Security validation

Before publishing, the repository was scanned for exposed credentials.

Tool used:

Gitleaks

Result:

No leaks found

Command example:

gitleaks detect . --no-git

Security lesson:

Always scan before publishing.

Do not assume a local repository is clean.

## GitHub workflow

The repository was created and updated from Linux terminal.

Workflow:

git add README.md

git commit -m "Update guide"

git push origin main

The guide was not manually edited from the GitHub web interface.

## Lessons learned

The installation was not the hardest part.

The difficult part was understanding the interaction between:

- OpenClaw
- gateway
- model providers
- Ollama
- local services
- hardware limits
- skills
- automation
- Telegram
- security

The correct workflow was:

Install

↓

Test

↓

Fail

↓

Debug

↓

Fix

↓

Retest

↓

Document

↓

Scan

↓

Publish

## Project status

This repository is a field guide based on real testing.

It will continue improving as the local agent stack evolves.

## External technical review observations

The project received an external review focused on constrained hardware deployment.

Validated conclusions:

OpenClaw and inference models should be treated as separate components.

Hardware limitations strongly influence deployment architecture.

Security validation before publication is mandatory.

Real-world testing is more valuable than theoretical recommendations.

Some optimization suggestions remain future work and require validation inside the actual environment.

