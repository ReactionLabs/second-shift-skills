# Second Shift Skills Library

A free, open library of agent skills, hosted by Second Shift. Every skill
here is a single `SKILL.md` file an AI agent can read and follow: packaged
know-how for marketing, sales, research, design, and running a business.
No account, no paywall, no catch.

**The library's home:** https://secondshiftos.com/skills

## For agents

Do not scrape this repo page by page. Read the machine-readable index
first, pick a skill by its description and its what-it-can-touch line,
then fetch the raw `SKILL.md` from its stable URL:

- Index: https://secondshiftos.com/skills/index.json
- Raw skill: `https://secondshiftos.com/skills/<slug>.md`
- Start with the library's own guide skill, `find-second-shift-skills`,
  which teaches the library's conventions.

The same index also lives at the root of this repo as
[index.json](index.json), and every skill lives in a folder of its own
(`<slug>/SKILL.md`), byte-identical to the file the site serves.

Install with the open skills CLI:

```bash
npx skills add <owner/repo> --skill <slug>
```

Each entry in the index carries its exact install command.

## The two classes (and a third that plugs in)

- **Works anywhere** — general skills that run in any agent's own
  environment, on the user's own files and accounts.
- **From Second Shift** — first-party skills written by Second Shift
  about the library and its conventions.
- **Plugs into Second Shift** — first-party skills that work through a
  Second Shift account, inside the permissions the account owner granted.

## The rule

**A skill teaches. It never grants permission.**

Installing a skill gives an agent a playbook, nothing more. What an agent
may actually read, change, send, or mint on a Second Shift account is
decided by the account owner's own permission toggles, skill or no skill.

## How skills get in

Every mirrored skill in this library was read in full by the Second Shift
fleet before listing, checked for credential demands, cookie or session
access, and anything exfiltration-shaped, and mirrored byte-identical
from an upstream repository carrying an MIT or Apache-2.0 license. The
table below records each skill's source and license exactly. First-party
skills are written by Second Shift and marked as such.

## The catalog (62 skills)

| Skill | Shelf | Class | Source | License |
|---|---|---|---|---|
| [Find Second Shift Skills](find-second-shift-skills/SKILL.md) | Start here | From Second Shift | Second Shift (first-party) | MIT |
| [Agent Reach](agent-reach/SKILL.md) | Research | Works anywhere | [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) `agent_reach/skill/ (English edition)` | MIT |
| [Prospecting](prospecting/SKILL.md) | Prospecting & lead finding | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/prospecting/` | MIT |
| [Frontend Design](frontend-design/SKILL.md) | Design & UI | Works anywhere | [anthropics/skills](https://github.com/anthropics/skills) `skills/frontend-design/` | Apache-2.0 |
| [Design Taste (Frontend)](design-taste-frontend/SKILL.md) | Design & UI | Works anywhere | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) `skills/taste-skill/` | MIT |
| [Design Engineering](emil-design-eng/SKILL.md) | Design & UI | Works anywhere | [emilkowalski/skills](https://github.com/emilkowalski/skills) `skills/emil-design-eng/` | MIT |
| [SEO Audit](seo-audit/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/seo-audit/` | MIT |
| [Social Media](social/SKILL.md) | Social media | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/social/` | MIT |
| [Video Production](video/SKILL.md) | Social media | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/video/` | MIT |
| [Community Marketing](community-marketing/SKILL.md) | Social media | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/community-marketing/` | MIT |
| [Influencer Marketing](influencer-marketing/SKILL.md) | Social media | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/influencer-marketing/` | MIT |
| [Public Relations](public-relations/SKILL.md) | Social media | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/public-relations/` | MIT |
| [Event Marketing](events/SKILL.md) | Social media | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/events/` | MIT |
| [Content Strategy](content-strategy/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/content-strategy/` | MIT |
| [Copywriting](copywriting/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/copywriting/` | MIT |
| [Copy Editing](copy-editing/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/copy-editing/` | MIT |
| [AI SEO](ai-seo/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/ai-seo/` | MIT |
| [Programmatic SEO](programmatic-seo/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/programmatic-seo/` | MIT |
| [Link Building](link-building/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/link-building/` | MIT |
| [Schema Markup](schema/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/schema/` | MIT |
| [Site Architecture](site-architecture/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/site-architecture/` | MIT |
| [Competitor Comparison Pages](competitors/SKILL.md) | Content & SEO | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/competitors/` | MIT |
| [Marketing Images](image/SKILL.md) | Design & UI | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/image/` | MIT |
| [Product Marketing Context](product-marketing/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/product-marketing/` | MIT |
| [Marketing Ideas](marketing-ideas/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/marketing-ideas/` | MIT |
| [Marketing Psychology](marketing-psychology/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/marketing-psychology/` | MIT |
| [Marketing Plan](marketing-plan/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/marketing-plan/` | MIT |
| [Marketing Council](marketing-council/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/marketing-council/` | MIT |
| [Launch Strategy](launch/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/launch/` | MIT |
| [Offer Design](offers/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/offers/` | MIT |
| [Pricing Strategy](pricing/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/pricing/` | MIT |
| [Co-Marketing](co-marketing/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/co-marketing/` | MIT |
| [Marketing Loops](marketing-loops/SKILL.md) | Marketing strategy | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/marketing-loops/` | MIT |
| [Customer Research](customer-research/SKILL.md) | Research | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/customer-research/` | MIT |
| [Competitor Profiling](competitor-profiling/SKILL.md) | Research | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/competitor-profiling/` | MIT |
| [Reverse-Engineer Marketing](reverse-engineer-marketing/SKILL.md) | Research | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/reverse-engineer-marketing/` | MIT |
| [Cold Email](cold-email/SKILL.md) | Sales & outreach | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/cold-email/` | MIT |
| [Sales Enablement](sales-enablement/SKILL.md) | Sales & outreach | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/sales-enablement/` | MIT |
| [RevOps](revops/SKILL.md) | Sales & outreach | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/revops/` | MIT |
| [Email Sequences](emails/SKILL.md) | Email & lifecycle | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/emails/` | MIT |
| [SMS Marketing](sms/SKILL.md) | Email & lifecycle | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/sms/` | MIT |
| [Conversion Rate Optimization](cro/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/cro/` | MIT |
| [Signup Flow Optimization](signup/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/signup/` | MIT |
| [Popups & Overlays](popups/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/popups/` | MIT |
| [Paywalls & Upgrade Screens](paywalls/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/paywalls/` | MIT |
| [Onboarding & Activation](onboarding/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/onboarding/` | MIT |
| [A/B Testing](ab-testing/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/ab-testing/` | MIT |
| [Lead Magnets](lead-magnets/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/lead-magnets/` | MIT |
| [Referral & Affiliate Programs](referrals/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/referrals/` | MIT |
| [Free Tools Strategy](free-tools/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/free-tools/` | MIT |
| [Churn Prevention](churn-prevention/SKILL.md) | Growth & conversion | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/churn-prevention/` | MIT |
| [Paid Ads](ads/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/ads/` | MIT |
| [Ad Creative](ad-creative/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/ad-creative/` | MIT |
| [Analytics Tracking](analytics/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/analytics/` | MIT |
| [Attribution](attribution/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/attribution/` | MIT |
| [Conversion Tracking](conversion-tracking/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/conversion-tracking/` | MIT |
| [App Store Optimization](aso/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/aso/` | MIT |
| [Directory Submissions](directory-submissions/SKILL.md) | Ads & measurement | Works anywhere | [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) `skills/directory-submissions/` | MIT |
| [Build a Campaign](build-a-campaign/SKILL.md) | Campaigns | Plugs into Second Shift | Second Shift (first-party) | MIT |
| [Social Media Scheduling](social-media-scheduling/SKILL.md) | Social media | Works anywhere | Second Shift (first-party) | MIT |
| [Research](research/SKILL.md) | Research | Works anywhere | [mattpocock/skills](https://github.com/mattpocock/skills) `skills/engineering/research/` | MIT |
| [Brainstorming](brainstorming/SKILL.md) | Building & planning | Works anywhere | [obra/superpowers](https://github.com/obra/superpowers) `skills/brainstorming/` | MIT |

## License and attribution

This repository is a mirror and catalog, not a relicensing. Each skill
keeps its own upstream license and copyright, recorded per skill in the
table above and in [LICENSE](LICENSE). Check a skill's license before
redistributing it further.
