---
name: tarpit
description: Pressure-tests a startup or hackathon idea before code: names the first customer, checks YC tarpit patterns, network cold-start risk, YC Requests for Startups, and demo scope. Use when validating, picking, or stress-testing an idea, or asked "is this a tarpit" or "what should we build".
---

# Tarpit check

A tarpit looks open but has killed many capable founders for a structural market reason.
Find that reason before the team spends its hours.

Inputs (ask once, only for what is missing): the idea, the customer, the timebox.
Garaža defaults: 40 hours, 4 people, advanced.

Mode: direct by default; give the verdict and the strongest objection first. If the user
says "Socratic", ask one question at a time and give no verdict until the team states one.
Never flatter.

## Steps

1. **Customer.** Do not continue until the team names one real person or a narrow role
   (good: "owner of a 60-person food distributor in Zagreb who reconciles invoices by
   hand"). Ask what that person does today (the real competitor), what the problem costs
   them per week, and what they literally said when asked. Recommend 3 conversations
   before code; drafts only, never send.
2. **Patterns.** Read [references/patterns.md](references/patterns.md). Match by mechanism;
   a keyword is only a hint. Niche or underserved audiences are not tarpits.
3. **Graveyard.** Web-search 2 to 5 companies that tried this exact idea; say what killed
   each and how any survivor escaped. Cite sources; never name dead companies from memory.
4. **Frontier.** Name the specific measured change (capability, cost, law, channel) that
   removes the old cause of failure. "AI exists" fails. If needed, use `first-principles`.
5. **Cold start.** Only if value needs two sides or many users: does one user get value
   alone? If not, find the single-player tool inside it, or the team acts as the supply.
6. **RFS.** Fetch `https://www.ycombinator.com/rfs`; report up to 3 overlaps. If the fetch
   fails, use [references/rfs.md](references/rfs.md) and say it may be stale. A match is
   no validation of the idea.
7. **Scope.** Person-hours = hours × people (× 0.4 beginner, × 1.3 advanced). Under 20:
   one interaction; 20 to 60: one loop a stranger can use; over 60: one loop plus one
   delightful detail. Cut login, database, payments, and admin; fake them. If a feature is
   not in the 60-second demo, cut it. Build the least-known part first.

Loop back after any pivot.

## Output

```text
Idea:       one line
Customer:   unspecified | vague | plausible | named, with the person or role
Tarpit:     high | moderate | none, with the matched mechanism
Graveyard:  named attempts, cause of death, sources
Frontier:   the specific change, or none
Cold start: single-player value yes/no, and the escape
RFS:        overlaps with season, or none
Scope:      person-hours and the one-sentence demo
Weakest:    the premise most likely wrong, with confidence
Next:       the cheapest test before code
```
