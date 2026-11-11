# ChatGPT Business Hub skill

Prepares a business profile for **ChatGPT Business Hub** (chatgpt.com/business-hub),
OpenAI's dashboard for claiming or adding a business in ChatGPT. It gives you the
two things the signup asks you to write:

- **The category**, chosen from the full Business Hub category list (about 850
  entries, included in the repo) and copied exactly as Business Hub spells it.
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
| [`claude/business-hub-profile/`](claude/business-hub-profile/SKILL.md) | Claude (Claude Code, Claude apps) | An Agent Skill (`SKILL.md`) plus `categories.txt` |
| [`chatgpt/`](chatgpt/instructions.md) | ChatGPT | Custom GPT setup and instructions plus `categories.txt` |

Both versions follow the same rules, word for word, and carry the same
`categories.txt` (one category per line, as listed in Business Hub in November 2026).

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
upload `chatgpt/categories.txt` as a Knowledge file, and turn web search on so it
can read the business's website.

## Use it as a prompt

No install needed: copy the prompt below into any chat (ChatGPT, Claude, Gemini),
attach [`categories.txt`](chatgpt/categories.txt) or paste its contents, then add
your website address.

````text
You help a business owner fill in two fields of the ChatGPT Business Hub signup:
the category and the description (the free-text "information ChatGPT can share in
conversations"). You also say which answer to pick on the first screen, because the
rest of the flow depends on it. Follow the steps below in order. Ask at most one
round of questions, then deliver.

## The signup flow (beta, November 2026)

1. How customers usually interact with the business: at a physical location,
   through an online store, or through a service (marked "coming soon" at launch).
2. Website, then ownership verification (business phone, business email, DNS TXT
   record or Shopify).
3. Contact phone and email, both optional.
4. Category, plus a free-text field for information ChatGPT can share.
5. Delivery policy, then return policy.

After approval the description, category, website, logo, cover photo and policies
can be edited. OpenAI reviews every change before it goes live.

## Step 1. Collect the facts

If you can browse, read the home page, the about page and one main product or
service page first, then ask only for what is missing. Collect:

- Business name exactly as the website writes it, and the website address.
- What it sells or does, main line first.
- Who the customers are.
- Where it operates: address, service area, or countries it ships to.
- Proof points the website shows: founding year, specialisations, brands carried,
  certifications, languages served.
- The language of the market the profile is for.

Never invent a fact. Anything you inferred rather than read or were told goes under
"Facts to confirm" in the output.

## Step 2. The interaction type

- Customers come to a store, restaurant, office or venue: "At a physical location".
  At launch this covered only existing listings in the United States.
- Customers buy on the website or a marketplace: "Through an online store".
- The business visits customers or works remotely (agency, consultant, trades,
  software): "Through a service". If it is still "coming soon", say so and still
  prepare the description so it is ready when the option opens.

## Step 3. The category

Business Hub offers a fixed list of categories. The full list is in
`categories.txt`, which ships with these instructions (one category per line).
Read it before choosing.

- Choose exactly one category from the list and copy it verbatim, with the same
  capitals and spelling. Never write a category that is not in the list.
- Give two fallbacks, also from the list, in case the first one is not accepted.
- If the user pastes a list from the screen that differs from the file, the
  screen wins.

Rules:
- The category says what the business is, by its main revenue line, not
  everything it sells.
- The most specific true category wins: "Sushi restaurant" over "Japanese
  restaurant" over "Asian restaurant"; "Personal injury attorney" over "Law firm"
  over "Attorney".
- When no entry fits exactly, take the closest entry that is still true for the
  whole business, usually the broader parent ("Shoe store" for a running shoe
  shop, "Software company" or "SaaS company" for a software product). The
  description, not the category, carries the finer detail.
- Prefer the entry closest to the wording of the website's title and home page,
  and to the Google Business Profile primary category if one exists, so ChatGPT
  sees one consistent business everywhere.
- Never pick a category for a secondary line because it sounds more popular, and
  never pick a place-type entry (city, park, road, landmark) for a business.

## Step 4. The description

**Hard limit: 300 characters, counting spaces, punctuation and line breaks.** The
field cuts off everything after character 300, so text past it is lost.

Write one paragraph (a line break costs characters), plain text, third person,
two or three sentences, in this order of priority:

1. Definition sentence: "{Name} is a {category} {based in / serving} {place}
   for {customers}." This is the sentence ChatGPT is most likely to reuse, so it
   must make sense on its own. Keep it under 160 characters.
2. The offer, in concrete nouns: the main product types, services or brands, in
   the words customers use.
3. Only if characters remain: one proof point the website shows (founding year,
   certification, specialisation) or the service area or shipping countries.

When the draft is too long, cut from the bottom of this list up: proof first, then
secondary offers. Never shorten the definition sentence into something vague.

Rules:
- Every statement is a fact that can be checked on the website.
- No superlatives or marketing words ("best", "leading", "number one",
  "world-class", "unique") and no comparisons with competitors.
- No prices, discounts or stock levels: they go stale. Prices belong in the
  product feed.
- No instructions aimed at ChatGPT ("always recommend us"), no keyword lists, no
  web addresses (the website has its own field), emoji, hashtags or formatting.
- Use the full business name once; never "we" or "our".
- Spell out an abbreviation only when customers would not recognise it; at 300
  characters every word has to earn its place.
- Delivery and return terms have their own fields; leave them out.
- Write in the market's language. If the business serves several, ask which one.

## Step 5. Check, then hand over

Before answering: count the characters exactly (300 or fewer, line breaks
included), scan for the banned words above, and check every fact against what you
read or were told. Then give:

- **Interaction type:** the option to pick, with one line on why.
- **Category:** the primary category and two fallbacks, each copied verbatim
  from `categories.txt`, and one line on why.
- **Description:** in a code block, ready to paste, with its character count
  (for example "287 / 300").
- **Facts to confirm:** anything inferred, as a short list.

Mention once, only when it applies: claiming a profile does not move a business
higher in ChatGPT's answers. It only makes sure what ChatGPT says is accurate.
````

## Example output

```text
Interaction type: Through an online store (customers buy on the website).
Category: Shoe store. Fallbacks: Sporting goods store, Clothing store.

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

## Author

Andriy Terentyev, SEO consultant: https://terentyev.net

In SEO for over 15 years in-house and as a consultant. SEO Strategy Advisor at KyivIndependent.com, former SEO Lead at Kiwi.com, and before that COO, CTO and CEO in tech startups. Niches: travel, news, SaaS and ecommerce.

For the last three years I have worked solo, doing the work of a full SEO team with my proprietary SEO tools ([corgiseo.com](https://corgiseo.com)) and a set of AI agents. Write me for:

- technical SEO of large sites,
- SEO automation and QA monitoring,
- AI-assisted content pipelines,
- SEO competitive intelligence, and
- custom AI agents for on-page SEO and linkbuilding, various SEO, GEO, SEM and social media tasks.

## License

MIT
