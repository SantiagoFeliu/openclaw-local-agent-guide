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
