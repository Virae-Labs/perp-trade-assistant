# Perp Trade Assistant

Prepare official Hyperliquid, Lighter and dYdX perpetual order forms from a Dashboard `browser-hedge-v1` instruction. The user completes wallet connection, authorization, setting changes and final order submission.

This repository contains one skill, defined by `SKILL.md` at its root. A connected browser tool for the user's existing Chrome profile is required. Installing this skill does not grant browser access or technically enforce fill-only permissions.

Install this repository as `perp-trade-assistant` using your AI client's supported skill installer or personal skills directory. The repository is `Virae-Labs/perp-trade-assistant`; private repository access is required. Invoke `$perp-trade-assistant` with the copied Dashboard instruction. Never add API credentials or wallet material to the repository.

Dashboard tracks read-only position observations after explicit user association. Net position snapshots do not establish individual executions, fees or historical funding. Existing target exposure is rejected in the first version. Skill instructions do not replace restricted browser tools or user review.
