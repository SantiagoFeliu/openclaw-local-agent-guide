# Build a Completely Free OpenClaw AI Agent on Linux with Ollama + Telegram

Build a completely free local AI agent using OpenClaw, Ollama, Telegram and workflow automation on Linux.

A real-world, fully reproducible guide based on actual debugging, failures and deployment experience.

This repository exists because building a working OpenClaw system was very different from watching tutorials or reading documentation.

The process required multiple days of testing, debugging, architecture changes and validation before obtaining a stable result.

The objective:

Help other people avoid losing days repeating the same mistakes.

## Environment used

Operating System: Linux Mint

GPU: NVIDIA GTX 1650 4GB

Local LLM Runtime: Ollama

Primary model: Qwen2.5

Agent framework: OpenClaw

Automation: n8n

Integration: Telegram

Execution mode: Local only

Paid APIs: None

## Architecture

Linux Mint

↓

OpenClaw

↓

Gateway

↓

Ollama

↓

Qwen2.5

↓

Skills

↓

n8n

↓

Telegram

## Validation workflow

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

Automate

## Rules

No paid APIs

No fake one-click claims

No undocumented shortcuts

Everything validated in a real environment

## Real deployment journey

The actual installation process was not linear.

The following stages happened during real deployment:

### Phase 1

Linux Mint preparation

Node installation using NVM

Environment validation

OpenClaw installation

Version updates

### Phase 2

Gateway service investigation

systemd user services

Port validation

127.0.0.1:18789

### Phase 3

Ollama deployment

Model testing

Qwen experiments

Performance validation

GTX1650 limitations

### Phase 4

OpenClaw internal investigation

~/.openclaw

openclaw.json

sessions

logs

providers

agent configuration

### Phase 5

Skills investigation

skills check

skills list

skills info

58 installed skills discovered

safe custom skills research

### Phase 6

Telegram integration

Bot routing

communication tests

agent response validation

### Phase 7

n8n integration

workflow generation

automation tests

local orchestration

### Phase 8

Failures and debugging

provider conflicts

schema failures

service crashes

gateway issues

manual fixes

### Lessons learned

Documentation alone was not enough.

Validation inside the real environment was required.


## Real validation commands used during deployment

The system was repeatedly validated from terminal.

Examples:

systemctl --user status openclaw

systemctl --user status openclaw-gateway

systemctl --user status ollama

ss -tulpn | grep 11434

ss -tulpn | grep 5678

curl http://localhost:11434/api/tags

curl http://localhost:8002/health

openclaw skills check

openclaw skills list

openclaw skills info github

cat ~/.openclaw/openclaw.json

grep -R "provider\|model" ~/.openclaw

## Important observation

The installation itself was easy.

Understanding what OpenClaw was actually doing internally took significantly more time.

