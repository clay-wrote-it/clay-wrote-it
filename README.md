# Hi, I'm Christian 👋

I build and operate **[Docket Pro](https://docketpro.ai)**, a court-records intelligence product for Davidson County, Tennessee.

## Docket Pro

Docket Pro helps attorneys, legal researchers, and law schools answer practical questions from historical court data, like how a judge tends to rule, how opposing counsel's cases usually turn out, and how costs and outcomes change over time. It has unified search across cases, people, attorneys, and appearances, an analytics library, saved searches and alerts, and an AI research assistant that answers natural-language questions with charts.

**My role:** founder and sole engineer. I own product, design, the full-stack codebase, the data model, billing, and operations.

**Stack:** TypeScript · React + Vite + Tailwind/shadcn/ui · Node.js/Express · PostgreSQL (Neon) + Drizzle ORM · Postgres trigram (pg_trgm) search · Anthropic Claude API (tool-use) · Stripe · Replit deployments

**A hard problem: one person, many spellings.** The same party or filing can show up as `LAST, FIRST M.` in one record and `First M. Last Jr.` in another, and the same filing can arrive more than once with only cosmetic differences. At scale, Docket Pro has to:

- normalize party names so search and analytics count one person once, not five times
- dedupe filings on normalized fields rather than raw text, without merging real, distinct events in the same case
- keep the search index current as new records arrive, using trigram indexes defined in the schema so a migration can't silently drop them

Production code is private. For a small, self-contained example of how I approach normalization and dedup, see the public sample below. I'm happy to walk through the architecture in conversation.

## Public sample

📌 **[court-records-sample](https://github.com/clay-wrote-it/court-records-sample)**: a TypeScript normalizer and deduper for docket-style entries, with a typed data model and unit tests. All fixture data is fake.
