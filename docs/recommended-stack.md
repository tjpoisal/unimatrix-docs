# Recommended stack

This page lists infrastructure and developer tools that fit Unimatrix users: people connecting MCP clients, building agents, or self-hosting with Docker and PostgreSQL (pgvector).

It is public documentation, not a paid placement until a tracking URL is filled in. The live product docs at [deployunimatrix.com/docs](https://www.deployunimatrix.com/docs) are served from the closed-source product app; this repository does not automatically update that site.

## Affiliate disclosure

Some links on this page may be affiliate links. If a referral URL is configured in [`affiliates.json`](affiliates.json) and you buy through it, Unimatrix may earn a commission, at no extra cost to you. That compensation could affect how you weigh a recommendation. Until a tracking URL is added, the links below go to the official product sites and are not paid links.

See [16 CFR 255.5](https://www.ecfr.gov/current/title-16/chapter-I/subchapter-B/part-255) (material connections must be clearly and conspicuously disclosed).

## How to add a referral ID

1. Complete the program's own signup (tax forms are required for US payouts).
2. Copy the full tracking URL from the program dashboard.
3. Paste it into the `affiliateUrl` field for that program in [`affiliates.json`](affiliates.json). Leave the field as `""` until you are approved.
4. Never commit passwords, API keys, or tax identifiers.

## Recommended tools

### Hosting and deploy

- **Railway** — Straightforward deploys for side projects and small services. The official affiliate program pays 15% of a referred customer's invoices for the first 12 months and requires only a Railway account ([program docs](https://docs.railway.com/community/affiliate-program)). Self-hosting Unimatrix itself is an Enterprise option discussed under agreement; Railway is a fit for related apps and supporting services.
- **DigitalOcean** — Droplets, managed databases, and app hosting if you want a conventional VPS or a Postgres host. Official program: 10% of monthly spend for 12 months ([affiliates](https://www.digitalocean.com/affiliates)).
- **Namecheap** — Domains, hosting, and TLS certificates. Commissions apply to a new customer's first eligible order ([rates](https://www.namecheap.com/support/knowledgebase/article.aspx/9933/55/what-are-the-namecheap-commission-rates/), [signup](https://www.namecheap.com/affiliates/)).

### Data and AI applications

- **PostgreSQL with pgvector** — This is what Unimatrix self-hosting targets (PostgreSQL 16 in current docs). There is no affiliate program for PostgreSQL itself.
- **Pinecone** — A hosted vector database for other AI apps that need a dedicated vector store. Official PartnerStack offer: 10% of a qualifying customer's first-year revenue, capped at $1,200, with a 180-day referral period ([agreement](https://www.pinecone.io/partners/affiliate-agreement.pdf), [apply](https://dash.partnerstack.com/application?company=pinecone&group=affiliateprogram)). Unimatrix hosted memory does not require Pinecone.

### What we are not listing here

- **Vercel** and **Cloudflare** — no current public cash affiliate program we could verify on their official pages.
- **Supabase** — the public partners page describes unpaid Integration and Solution tracks, not a cash affiliate program.
- Adult-site placements — several of these programs restrict adult or obscene marketing. These links are for deployunimatrix.com documentation only.

## Official signup URLs

Use the URLs in [`affiliates.json`](affiliates.json). Fill `affiliateUrl` only after approval.
