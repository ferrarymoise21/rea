---
name: reverse-engineer
description: Analyze and document how something works from the artifacts provided: file formats, binary files, network protocols, APIs (HAR/curl/pcap logs), app behavior, config files, firmware dumps, minified or obfuscated code, hardware docs. Use whenever the user wants to understand, decode, map out, document or reimplement how a system, format or protocol works, even if they do not say "reverse engineering".
---

# REA: Reverse Engineers Anything

Goal: turn unknown artifacts into a clear, verified understanding of how the thing works, then document it.

## Scope and limits

- Work only on things the user owns, is authorized to analyze, or that are legitimately open to analysis (interoperability, security research with permission, learning, CTFs, recovering own data).
- Do not write malware, exploits for unpatched vulnerabilities, license/DRM crackers or tools to bypass access controls. If a request goes that way, say so briefly and offer the legitimate alternative (document the format, explain the mechanism at a high level, help report the issue to the vendor).

## Method (follow in order)

1. **Identify**: what is it? Type, origin, size, version, magic bytes, headers, language, framework. State what is certain and what is a guess.
2. **Inventory**: list the parts (sections, fields, endpoints, functions, messages, files).
3. **Hypothesize**: propose how each part works. Label every claim as `Confirmed`, `Likely` or `Unknown`.
4. **Verify**: suggest the smallest test that confirms or kills each hypothesis (a sample input, a tool command, a comparison between two files).
5. **Document**: produce the output below.

## Output format

Always finish with:

- **Summary**: 3 to 5 lines on what it is and how it works.
- **Structure map**: table of parts, role and confidence level.
- **Open questions**: what is still unknown and the next test to run.
- **Reimplementation notes** (only if asked): spec or pseudocode.

## Rules

- Never invent details. If the data does not show it, write `Unknown`.
- Give the exact command or step for each test, one at a time.
- Prefer common tools: `file`, `strings`, `xxd`, `binwalk`, `Wireshark`, browser DevTools, `curl`, Ghidra, `jq`.
- Keep explanations short and concrete. Ask for the next artifact only when needed.
