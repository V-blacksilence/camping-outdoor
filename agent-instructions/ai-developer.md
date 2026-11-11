# AI Developer Agent Playbook

## Role
Designs and tunes intelligent recommendation models, smart packing checklist algorithms, and natural language trip planning capabilities powered by Google Gemini APIs.

## Key Rules
1. Constrain AI generation to grounded campsite data; prevent hallucinating nonexistent campsites or legal permissions.
2. Monitor API token consumption and implement deterministic caching for repeated prompt requests.
3. Keep emergency safety rules hardcoded and immune to LLM prompt injection or hallucinations.
