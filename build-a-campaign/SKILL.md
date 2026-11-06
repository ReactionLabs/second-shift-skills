---
name: build-a-campaign
description: Build a complete local-business campaign as a ready-to-run pack the owner approves before anything sends. Use when a business owner wants to promote an offer to their existing customers or leads: pick the audience, frame the offer, write the announcement, the follow-ups, and the last call, add a tracked QR hook where one is available, set the send calendar, and finish with how the owner will see what it produced.
license: MIT
metadata:
  author: Second Shift
---

# Build a Campaign

This skill produces one thing: a campaign pack. The pack is the whole
campaign, written out and ready to run, that the owner reads and approves
before a single message goes anywhere.

A campaign is not a Second Shift feature. Second Shift has no campaign or
sequence tool, for tenants or anyone else, and nothing in this skill sends.
What Second Shift provides, for a business that is a tenant, is the pipe:
its leads, its analytics summary, and its QR codes. Everything else in a
campaign, the writing, the calendar, and the sending itself, happens with
the owner's own tools and accounts.

## What runs where

- Through Second Shift (tenant accounts only, and only inside the
  permissions the owner granted their connection): reading the lead list,
  reading the analytics summary, minting a QR code. Minting is a mint-class
  action: the owner approves it, the way the pipe already enforces.
- On the owner's own tools: holding the customer list if the business is
  not a tenant, hosting the landing page a QR code points at, and all
  sending (email, text, or social) once the pack is approved.
- If a step needs a pipe permission the owner has not granted, the step
  degrades to the owner's own tools and the pack says so. Never work around
  a missing grant.

## Start with three inputs

You need a business, an offer, and a goal. If any of the three is missing
or vague, ask for it before writing anything. Never invent an offer, a
price, or a deadline to fill the gap.

## Step 1: Pick the audience

Ask about the list before you touch copy: who is on it, how they got
there, and when they last heard from the business. A list of past customers
and a list of people who asked once and went quiet are different audiences
and get different campaigns.

If the business is a Second Shift tenant, pull the picture from the pipe
under the owner's granted permissions: the leads on file and the analytics
summary (where visitors come from, what they do). Read only. The audience
you name in the pack should be one the owner recognizes as theirs.

## Step 2: Frame the offer

One offer, one audience, one deadline. Write the offer the way the owner
would say it out loud: what it is, who it is for, what it costs, when it
ends. Terms the owner has not confirmed do not go in. If the offer cannot
be said plainly in two sentences, it is not framed yet.

## Step 3: Write the copy set

Write every message in full, not as outlines:

1. The announcement: the offer, why now, the one action to take.
2. Follow-up one: a new angle or a real detail, not the announcement
   repeated louder.
3. Follow-up two: shorter. Answers the obvious objection or question.
4. The last call: the deadline, stated once, honestly.

Rules for every message: plain words, one ask per message, and claims
only from facts the owner gave you. No invented results, no borrowed
testimonials, no numbers you cannot point to. If a claim would make the
campaign stronger but you cannot source it, leave it out and tell the
owner what proof would let you use it next time.

## Step 4: Choose the hook

Every campaign needs one tracked way in. Where the setup allows it, that
is a QR code pointing at the campaign's landing page: on a counter card,
a flyer, a receipt, a door hanger, or inside the messages themselves.

If the business is a Second Shift tenant, mint the QR code through the
pipe, with the owner's approval, pointed at the landing page URL. If it is
not a tenant, use the owner's own QR tool or a plain short link, and say
in the pack which one you used. A hook you cannot track is a weaker hook;
name that honestly rather than pretending the numbers will show up.

## Step 5: Set the calendar

Lay out the send dates and times for the whole set before anything goes:
announcement, the follow-ups spaced days apart, the last call on the real
deadline. Note what stops the campaign early (the offer sells out, the
owner calls it off) and what happens to replies: who answers them, and how
fast. Replies the owner never sees are worse than no campaign.

## Step 6: Assemble the pack

The pack the owner approves contains, in this order:

1. The audience: who gets this, how many, where the list came from.
2. The offer as framed, with its deadline.
3. Every message, written in full, in send order.
4. The hook: the QR code or link, and where it will appear.
5. The calendar: every send date and time, and the early-stop conditions.
6. What is missing or assumed, stated plainly (an ungranted permission, a
   list of unknown size, a landing page still to build).
7. How the owner will see what it produced (next section).

Nothing sends until the owner has approved the pack. Approval of an
earlier campaign is not approval of this one.

## How the owner sees what it produced

End the pack with the measurement, in the owner's own terms: replies,
bookings, and redemptions the owner records, plus the tracked hook. For a
tenant, the pipe's analytics summary and lead list show the landing page's
visits and the new leads that arrived; that is traffic and leads, not a
campaign report, and Second Shift does not produce one. For a non-tenant,
name the report in the owner's sending tool where the same numbers live.
If a number cannot be seen anywhere, do not promise it.

## The ground rules

- Nothing sends without the owner's approval of this pack.
- A skill teaches. It never grants permission. Pipe reads and the QR mint
  happen only inside the owner's own Agent Access grants, and this skill
  changes none of that.
- Claims stay honest or they stay out.
