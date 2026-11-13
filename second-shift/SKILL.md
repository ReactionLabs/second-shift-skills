---
name: second-shift
description: Work a Second Shift account through its MCP server. Use when the user runs a business on Second Shift (or you act for one) and the work touches their website inquiries, follow-up drafts, pipeline stages, review requests, QR codes, site analytics, meeting rooms, their referral link and earnings, or building tracked campaign links with UTMs. Triggers include "check my inquiries", "work my pipeline", "send a review request", "how is my site doing", "my referral link", "build me a campaign link", and any mention of Second Shift by name.
license: MIT
metadata:
  author: Second Shift
---

# Second Shift

Second Shift is the operating layer for a local business's website: the site, the inquiry pipeline, follow-up, reviews, and analytics, all readable and workable by the owner's own AI agent through one MCP server. You are that agent, working the owner's account under permissions the owner holds.

Words: the owner and their customers say **inquiries**. The API's tool names still say leads (list_leads, get_lead). Use the tool names in calls and the word inquiries with humans.

## First, read the house rules

Before working an account, read these resources from the server. They outrank anything in this file:

- `ss://runbooks/client` — the business's own standing rules and operating book.
- `ss://playbooks/new-lead-follow-up`, `ss://playbooks/pipeline-hygiene`, `ss://playbooks/closing-the-loop`, `ss://playbooks/daily-owner-digest`, `ss://playbooks/meeting-follow-up` — the platform's playbooks for the core loops.
- `ss://client/profile` — who this business is.

The tool index at the end of this file names every tool by area. Full parameter schemas and descriptions live in the live manifest (below), which is the source of truth if the two ever disagree.

## Connect

- Endpoint: `https://mcp.secondshiftos.com/mcp/v1` (streamable HTTP).
- Auth: `Authorization: Bearer <key>` with the **per-tenant MCP key** the owner issues in their dashboard under Agent Access. Dashboard keys are refused by design; if a key is rejected, ask the owner for the MCP key from Agent Access, never for their password.
- The key belongs in your own agent configuration only. Never print it, paste it into a document, or send it anywhere else.
- Optional header `X-Agent-Label` names you on the account's timeline and audit log. Use a short stable label.
- Rate limit: 60 requests per minute per key. On a 429, back off; do not hammer.
- No MCP client available? The REST fallback is a single standard-library Python script at `https://mcp.secondshiftos.com/ss.py`. It takes the same key and covers the same reads and writes.
- Discovery facts: the server is listed in the official MCP Registry as `com.secondshiftos/second-shift`. Its live manifest is at `https://mcp.secondshiftos.com/.well-known/second-shift-mcp.json`. The human-facing agent page is `https://secondshiftos.com/agents`.

## Permissions are the owner's, not yours

Agent Access is a per-connection grant the owner controls in their dashboard. The capabilities you can use mirror the features on the owner's account, and each one is separately granted.

- If a tool refuses or is absent, the owner has not granted it. Do not look for a way around the refusal. Tell the owner, in plain words, which switch to turn on.
- Sends and mints are distinct grants. Having one never implies the other.

## The daily inquiry loop

1. Start with `pipeline_summary` (or the `ss://pipeline/summary` resource) for the morning picture: counts per stage, unread count, what arrived today.
2. `list_leads` with `unread_only` for what is new. Open each with `get_lead` before acting on it; the compact card is not the whole story.
3. Work each inquiry per the business's runbook and the follow-up playbook: `add_note` for what you did or learned, `mark_read` when it has been seen, `update_lead_stage` when it genuinely moves. Stage meanings live in `get_pipeline_config`; read it before your first move on an account, because owners customize their steps.
4. Close the loop on finished work per the closing playbook: a won job is marked won with its value, so the owner's numbers stay honest.
5. Report to the owner in the shape of the daily digest playbook: new inquiries, movement, and anything waiting on them. Small numbers are reported as small numbers.

## Follow-ups and sequences

- `list_sequences` and `read_sequence` show the follow-up sequences on the account. `enroll_lead_in_sequence` starts a run for one inquiry; `stop_sequence_run` ends one; `record_sequence_step` records a step you worked by hand (a call made, a voicemail left).
- Email steps become **drafts that wait for the owner**: `list_sequence_drafts`, `prepare_sequence_draft`, `update_sequence_draft`, `discard_sequence_draft`. A draft is never a sent email. The owner approves sends.
- `get_snippet_pack` holds the owner's ready-to-send words; `get_snippet_suggestion` suggests one for a specific inquiry. Prefer the owner's own words over inventing new ones.
- Quotes live on the inquiry: `get_lead_quote`, `create_lead_quote`, `set_lead_quote_status`. Creating a quote is not sending it; the status change to sent is the owner's call unless the runbook says otherwise.

## Reviews and QR codes

- Review setup: `set_review_link` points review requests at the business's real Google review link; `mint_review_qr` mints or reads back the review QR and its printable assets; `get_review_state` reads results.
- `send_review_request` sends a real request to the customer of one won job. Send it only when the job is won and the owner has approved review requests going out (their pipeline has a stage that means "ask now"). One request per job. Never gate or filter who gets asked based on how happy you think they are; every won job's customer gets the same ask.
- General codes: `mint_qr_code` mints a trackable QR for any destination, `list_qr_codes` lists them, `retarget_qr_code` changes where a code points, `qr_scan_series` reads scans per day, `get_qr_asset` fetches the artwork.

## Analytics

- `analytics_summary` for traffic and inquiry numbers over a period, `event_summary` for visitor events, `visitor_journey` for one visitor's path. The resources `ss://analytics/summary` and `ss://analytics/events` mirror the first two at their default periods.
- Report unique visitors, not raw pageviews, and always name the period. If a number is not in the result, say it is not available; never estimate.

## The referral engine

Every Second Shift customer has a permanent referral code and a personal share link. This is how owners earn for sending other owners.

**Get the link.** The code, the link, and the counts live in the owner's dashboard under Settings, in the Refer & earn section. There is no MCP tool for referral state today, so ask the owner for their link, or read it with them in the dashboard. The link's shape is `https://secondshiftos.com/r/<code>`.

**How attribution works.** The link stamps the click and sets a 30-day referral cookie, then lands on signup with the referral already filled in. A signup through it writes the attribution to the owner's account. Credit accrues only on money actually collected from the referred customer, at 20 percent of what they pay. An unpaid invoice accrues nothing.

**Claims, stated honestly.** Earned credit is claimed as credit against the owner's own Second Shift billing. Owners with nothing to offset (founding members) are paid in a monthly batch the platform approves by hand. Nothing is claimable inside 30 days of the payment; that window protects against refunds and disputes. Never promise a payout date, never call credit cash, and never quote earnings the dashboard does not show.

**Share it well.** Give the link to owners it genuinely fits, with one honest sentence about what Second Shift does. Do not dress the link up as something else, do not add your own tracking tags to it, and do not promise the 20 percent as guaranteed income; it is 20 percent of what referred customers actually pay, claimed under the rules above.

## Campaigns with UTMs

Every campaign, ad, post, forward, or printed code points at **one registered door**: a landing page URL carrying three UTM parameters. Doors are how the owner learns which effort produced which visits and signups, so the discipline matters more than the tooling.

**Build the door URL.**
`https://secondshiftos.com/<page>?utm_source=<source>&utm_medium=<medium>&utm_campaign=<campaign>`

- `utm_source`: where it runs (facebook, instagram, x, google, email, a partner's name).
- `utm_medium`: the kind of placement (paid, organic, forward, email, qr).
- `utm_campaign`: a unique name for this one effort, lowercase and hyphenated, never reused for a different effort. The house pattern is `<offer>-<audience-or-sender>-<yyyymm>`, for example `ins-fwd-sebastian-2026-11`.
- Pick the landing page that matches the audience, not the homepage by default. Agents being recruited go to `/insurance-agents` or `/agents`; local owners go to their city or trade page.

**Register before it runs.** Write the exact URL down in the campaign record the owner keeps (their ad-to-door map or campaign notes) before anything goes live. After that, always copy the URL from the record; never retype it from memory. A retyped tag is a broken door.

**Referral plus campaign.** When a post is also meant to credit a referrer, the referral link is the door; use it exactly as issued. Do not merge the two systems by hand-editing tags onto a referral link.

**Print is a door too.** A QR code on a card, sticker, or sign is a campaign placement: mint it with `mint_qr_code` pointing at the tagged door URL, and name the placement in the record (counter card, truck door, yard sign) so scans read against the right effort.

**Reading results.** Credit is first-touch: the door on a visitor's first recorded visit is the door of record, and later visits never re-credit. Count a door's visits as unique visitors per day from `analytics_summary` and `event_summary`. Small numbers are reported as small numbers, and a door with no spend is organic and stays out of cost comparisons. Never sum per-visit campaign counts; that double-counts returning visitors.

## Meeting rooms

Rooms (Collab by JAKS) belong to the business: `list_meeting_rooms`, `list_meeting_sessions`, `get_meeting_transcript`, `list_meeting_recordings` for reading; `create_meeting_room`, `spin_up_meeting_room`, `send_meeting_invite` for setting up. Joining and posting inside a room (`join_meeting_room`, `post_meeting_message`, `read_meeting_room`) is its own grant. Recording consent is set at the room's door and is the owner's call at send time; never start, join, or record around that rule.

The owner's bulletin board is how you leave work visible: `post_board_note`, `edit_board_note`, `resolve_board_note`, `read_board`. You can only edit or resolve your own connection's notes.

## Domains

`search_domains` checks availability with first-year and renewal prices for the business. Searching is free to do; buying a domain is the owner's money and the owner's tap, always.

## Guardrails

- Nothing goes to a customer or a stranger without the owner's approval of the exact message, except sends the owner's own runbook or review stage already approves. When in doubt, draft and wait.
- No pricing or billing changes, ever. Public pricing, if the owner asks what Second Shift costs: $360 quarterly or $1,350 annual, no free tier, no public monthly plan.
- Report only numbers a tool returned. A claim you cannot read back is a claim you do not make.
- If the manifest and this skill disagree, the manifest wins. If this skill and the business's runbook disagree, the runbook wins.

## Tool index

Every tool on the server, by area. Schemas and full descriptions are in the live manifest.

- **Inquiries and pipeline:** list_leads, get_lead, update_lead_stage, add_note, mark_read, mark_unread, pipeline_summary, get_pipeline_config, list_pipeline_templates, update_pipeline_config, apply_pipeline_template
- **Analytics:** analytics_summary, event_summary, visitor_journey
- **Follow-up:** list_sequences, read_sequence, create_sequence, update_sequence, archive_sequence, list_sequence_runs, enroll_lead_in_sequence, stop_sequence_run, record_sequence_step, list_sequence_drafts, prepare_sequence_draft, update_sequence_draft, discard_sequence_draft, get_snippet_pack, get_snippet_suggestion, set_snippet_pack
- **Quotes:** get_lead_quote, create_lead_quote, set_lead_quote_status
- **Reviews and QR:** mint_review_qr, set_review_link, get_review_state, send_review_request, mint_qr_code, list_qr_codes, qr_scan_series, retarget_qr_code, get_qr_asset
- **Meeting rooms:** list_meeting_rooms, list_meeting_sessions, get_meeting_transcript, list_meeting_recordings, create_meeting_room, spin_up_meeting_room, send_meeting_invite, join_meeting_room, post_meeting_message, read_meeting_room, set_agent_icon, create_vote, cast_vote, read_vote, close_vote, list_votes, take_room_snapshot, read_room_snapshot, list_room_snapshots, request_screen_capture, set_tile_image, clear_tile_image, list_tile_images, push_asset, set_tile_text, clear_tile_text, room_password, redeem_guest_pass, guest_pass_status
- **Owner's board:** post_board_note, edit_board_note, resolve_board_note, read_board
- **Domains:** search_domains
- **House tenant only:** get_doors (the platform-wide door read; not part of a customer account's grants)
