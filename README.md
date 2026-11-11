# ChatGPT Business Hub skill

Prepares a business profile for **ChatGPT Business Hub** (chatgpt.com/business-hub),
OpenAI's dashboard for claiming or adding a business in ChatGPT. It gives you the
two things the signup asks you to write:

- **The category**, matched to the options Business Hub shows you.
- **The description**, the free-text information ChatGPT can share about the
  business, kept within the field's **300-character limit** (spaces and line
  breaks included; the field cuts off everything after that).

It also tells you which answer to pick on the first screen ("How do customers
usually interact with your business?"), and lists any fact it had to infer so you
can confirm it before submitting.

The description is written for how ChatGPT reuses it: a first sentence that
defines the business on its own, then the offer in concrete words, then one proof
point. Facts only, no marketing words, no prices, no instructions aimed at ChatGPT.

## Two versions

| Folder | For | What it is |
| --- | --- | --- |
| [`claude/business-hub-profile/`](claude/business-hub-profile/SKILL.md) | Claude (Claude Code, Claude apps) | An Agent Skill (`SKILL.md`) |
| [`chatgpt/`](chatgpt/instructions.md) | ChatGPT | Custom GPT setup and instructions |

Both versions follow the same rules, word for word.

## Install

**Claude Code**

```bash
git clone https://github.com/internetyev/chatgpt-business-hub-skill.git
```

```bash
cp -r chatgpt-business-hub-skill/claude/business-hub-profile ~/.claude/skills/
```

Then ask Claude: "Prepare my ChatGPT Business Hub profile for example.com".

**Claude apps (claude.ai, desktop)**

Zip the `claude/business-hub-profile` folder and upload it under
Settings > Capabilities > Skills.

**ChatGPT**

Open [chatgpt/instructions.md](chatgpt/instructions.md) and follow it: create a
Custom GPT, paste the name, description, conversation starters and instructions,
and turn web search on so it can read the business's website.

## Example output

```text
Interaction type: Through an online store (customers buy on the website).
Category: Running shoe store. Fallbacks: Sporting goods store, Shoe store.

Northfield Running Co. is a running shoe store in Leeds, United Kingdom, for road and trail runners. It sells running shoes, clothing and accessories from Brooks, Hoka, Saucony and On, and offers free gait analysis in store. Founded in 2012.

241 / 300 characters

Facts to confirm: founding year (read from the footer), gait analysis is free.
```

(Northfield Running Co. is a made-up business.)

## Good to know

- Business Hub is in beta (launched November 2026), so screens and limits may
  change. If the field shows a different limit, follow the field.
- At launch, "Through a service" (agencies, consultants, trades, software) was
  marked "coming soon", and local stores could only claim an existing listing in
  the United States.
- Claiming a profile does not move a business higher in ChatGPT's answers. It
  makes what ChatGPT says about the business accurate.

## License

MIT
