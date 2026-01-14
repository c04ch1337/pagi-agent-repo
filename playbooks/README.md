# Playbooks Directory

This directory contains AI-generated playbooks distilled from successful agent task completions.

## How Playbooks Are Generated

1. The Memory Consolidator service queries Qdrant for successful task completions
2. Logs are sent to the LLM with a specialized "Distillation" prompt
3. The LLM creates step-by-step Markdown playbooks
4. Playbooks are automatically committed and pushed to this repository

## Playbook Structure

Each playbook includes:
- Task description and objectives
- Step-by-step procedures
- Best practices from successful completions
- Common pitfalls and how to avoid them
- Required tools and prerequisites

## Privacy

All playbooks are automatically filtered to remove sensitive information (IPs, usernames, internal server names) before being pushed to the repository.
