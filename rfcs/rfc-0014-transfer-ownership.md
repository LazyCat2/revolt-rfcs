- Feature Name: Transfer ownership
- Start Date: 03/03/2025
- RFC PR: #14
- Tracking Issue: https://github.com/revoltchat/backend/issues/196
- Status: accepted

# Summary

Change current owner of a server.

# Motivation

Currently ownership can only be transfered manually by Revolt team. That is not very good because you need to wait for a team member to check your email.

# Guide-level explanation

Instead of sending an email to Revolt team and waiting for answer, you would be able to transfer server ownership yourself in server settings.

# Reference-level explanation

Before transfering server ownership, there shold be folowing checks:
- A new server owner must be a server member. API should respond with `NotFound` otherwise.
- A new server owner must be a user. API will should respond with `InvalidOperation` if a new owner is a bot.
- Only server owner can transfer server ownership to others. API should respond with `NotOwner` if request was sent not by owner.

Changes in API:
- `PATCH /servers/:id` now accepts `owner` in it's body.

# Drawbacks

I do not see any drawbacks in this feature.

# Rationale and alternatives

Clients can implement server ownership transfer by adding a new button in server settings.

Design is the best because API already has an endpoint to edit server that can be used instead of creating a new separate endpoint just to change server ownership.

# Prior art

Discord already has feature to transfer server ownership. I'm not familiar with endpoint that does so.

# Unresolved questions

N/A

# Security concerns

Only server owner can transfer server ownership so server ownership cannot be "stolen" by anyone.
MFA or password is required to be provided so that a hacker with victim's token will not be able to steal server without password or MFA

# Future ideas

None
