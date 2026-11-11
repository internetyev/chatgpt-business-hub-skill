---
name: business-hub-profile
description: Prepare the business description (300 characters at most) and choose the category for registering or claiming a business in ChatGPT Business Hub (chatgpt.com/business-hub). Use when the user says "Business Hub", "claim my business in ChatGPT", "add my business to ChatGPT", "ChatGPT business profile", "write my ChatGPT business description", or "which category for ChatGPT".
---

# ChatGPT Business Hub profile

Produces two fields for the Business Hub signup: the category and the description
(the free-text "information ChatGPT can share in conversations"). Also says which
answer to pick on the first screen, because the rest of the flow depends on it.

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
- The category options shown on the Business Hub screen, if the user can paste them.
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

- If the user pasted the options: choose exactly one and copy it verbatim.
- Otherwise: give a primary category and two broader fallbacks for the user to type
  into the field and match against the suggestions.

Rules:
- The category says what the business is, by its main revenue line, not
  everything it sells.
- The most specific true category wins: "Running shoe store" over "Shoe store"
  over "Retail".
- Use the same wording as the website's title and home page, and the Google
  Business Profile primary category if one exists, so ChatGPT sees one consistent
  business everywhere.
- Never pick a category for a secondary line because it sounds more popular.

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
- **Category:** the primary category, two fallbacks, and one line on why.
- **Description:** in a code block, ready to paste, with its character count
  (for example "287 / 300").
- **Facts to confirm:** anything inferred, as a short list.

Mention once, only when it applies: claiming a profile does not move a business
higher in ChatGPT's answers. It only makes sure what ChatGPT says is accurate.
