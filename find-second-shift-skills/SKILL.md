---
name: find-second-shift-skills
description: Find and fetch skills from the Second Shift Skills Library. Use when a job might already have a packaged skill (prospecting, SEO, design, research, outreach, or a Second Shift business workflow) and you want to check the library before improvising. Teaches you to read the library's public index, pick a skill by its description, class, and what-it-touches line, and fetch the raw SKILL.md from its stable URL.
license: MIT
metadata:
  author: Second Shift
---

# Find Second Shift Skills

The Second Shift Skills Library is a free, open shelf of agent skills, hosted at
https://secondshiftos.com/skills. Anybody's agent can use it. There is no account,
no sign-in, and no paywall, for the human pages or for the machine surfaces below.

## Search the index first

Fetch the machine-readable index (one JSON document, versioned):

    GET https://secondshiftos.com/skills/index.json

Each entry carries: `slug`, `name`, `description` (the discovery trigger: what the
skill does and when to use it), `class` and `classLabel`, `touches` (a plain-words
line stating what the skill can read, change, or send), `source` (who wrote it and
where it lives upstream), `license`, `rawUrl`, and `installCommand`.

Read the index the way you read any skill list: names and descriptions first
(cheap), full files only for the skill you actually pick.

## Choose by class and by touch

- **Works anywhere** — general capability skills. They run in your own
  environment and imply nothing about Second Shift.
- **Plugs into Second Shift** — first-party business skills that work a Second
  Shift account through its MCP pipe. Their cards name the exact permissions
  they use.
- The `touches` line is the contract. If it says a skill never sends, it never
  sends. Check it before you fetch, not after.

## Fetch the skill

Every mirrored skill serves its exact bytes at a stable URL, no HTML chrome:

    GET https://secondshiftos.com/skills/<slug>.md

(the entry's `rawUrl` is authoritative). Save it as `SKILL.md` in a folder named
for the slug, in your agent's skills directory. Or install with the open skills
CLI using the entry's `installCommand` (for example
`npx skills add <owner>/<repo> --skill <name>`).

## The ground rule

A skill teaches an agent how to do something. It never grants permission to do
it. For skills that plug into Second Shift, the account owner's own Agent Access
grants decide what exists for their connection, and send-class and mint-class
actions stay behind the owner's own approval, exactly as the pipe enforces
without any skill installed. Installing a skill changes none of that.

## Licenses travel with the files

Each index entry names its license. Mirrored skills keep their upstream
copyright and license terms; check the `license` field before redistributing a
skill further. Skills marked as link-only in the index are not mirrored at all:
fetch those from their upstream repo under its own terms.
