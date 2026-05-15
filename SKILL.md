---
name: lavadev-toolkit
description: Use when executing any task in LobeChat. Ensures all tools are active via Tools Activator, and that User Interaction is used to collect any needed inputs before executing — with AI enhancement applied to every field before use.
---

# LavaDev Toolkit

## Core Rule

**Every task follows this exact pattern — no exceptions:**

```
1. Tools Activator → enable ALL tools
2. Identify what inputs are needed for this task
3. User Interaction → collect those inputs (if any are missing)
4. AI-enhance every collected input
5. Execute with enhanced inputs
```

---

## Step 1 — Always Enable All Tools First

At the start of every task, call **Tools Activator** and enable all available tools. Do not selectively pick. The full toolkit is always active:

> Agent Management, Agent Marketplace, Artifacts, Brief Tools, browser39-websearch,
> Calculator, Cloud Sandbox, discord-announcement-creator, Document, Documents,
> GitHub, GTD Tools, Knowledge Base, Lobe Agent, LobeHub, Memory, Message,
> Remote Device, Scheduled Tasks, Skill Maintainer, Skill Store, telegram-formatting,
> Topic Reference, Tools Activator, User Interaction, Web Onboarding, WebSearch

---

## Step 2 — Identify Missing Inputs

Before executing, check: does this task have any fields that are unspecified, ambiguous, or need a choice?

Examples of things that need collection:
- Names (repo name, channel, username, org, file name)
- Descriptions (what it does, what the message says)
- Options / choices (public vs private, recurring vs once, which org)
- Targets (which channel, which repo, which agent)
- Content (announcement body, commit message, task description)

If everything is already clear from the user's message → skip to Step 4.

---

## Step 3 — User Interaction for Input Collection

Use the **User Interaction** tool to collect anything missing. Rules:

- Ask all required fields in a single interaction — not one by one
- Use dropdowns / options where choices are finite (e.g. Public / Private, Yes / No)
- Use text fields for open-ended input (descriptions, names, content)
- Label every field clearly so the user knows what it's for
- Never ask for something that can be reasonably inferred or AI-generated

---

## Step 4 — AI-Enhance Every Input

After collecting, **never use raw user input directly**. Enhance everything:

| Input Type | How to Enhance |
|-----------|---------------|
| Project / repo name | kebab-case, descriptive, no abbreviations |
| Short description | Active voice, mentions purpose + stack, under 120 chars |
| Long description / README | Structured: what → why → features → stack → usage |
| Announcement / post body | Hook → detail → outcome → CTA, remove filler |
| Telegram content | Unicode styled text (NO raw `**` or `_`), punchy opener |
| Commit message | Conventional Commits: `type(scope): description` |
| Task / schedule label | `[Action] — [Target] @ [time]` |
| Agent prompt | Context → Task → Output format → Constraints |
| Any title | Clear, specific, searchable, properly cased |
| Any tag / topic list | Expand with related terms, lowercase, hyphenated |

When in doubt: make it more specific, more structured, and more useful than what the user typed.

---

## Step 5 — Execute

Run the task using the appropriate tool(s) with the enhanced inputs. Confirm result inline. No postamble.

---

## Quick Reference

```
ANY task
  └─ Tools Activator → all tools on
       └─ Missing inputs? → User Interaction → collect
            └─ Enhance every field
                 └─ Execute → done
```

---

## Common Mistakes

| Wrong | Right |
|-------|-------|
| Skipping Tools Activator | Always run it first, every task |
| Asking inputs one at a time | Collect all fields in one User Interaction call |
| Using raw user description | Always enhance before passing to any tool |
| Using `**bold**` in Telegram | Use Unicode styled text |
| Inferring a choice that needs confirmation | Ask via User Interaction |
| Asking something inferable | Don't ask — just enhance and fill it |
