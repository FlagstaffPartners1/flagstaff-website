# flagstaff-partners.com

The public website for Flagstaff Partners. Plain HTML/CSS, hosted on **Netlify**, code stored on
**GitHub** (organization: `FlagstaffPartners1`). The domain is registered at **GoDaddy**, which also
holds the DNS records that run company email (Microsoft 365).

## How to make a change (no coding needed)

1. Go to **claude.ai/code** and make sure you're signed in. Pick this repository
   (`FlagstaffPartners1/flagstaff-website`).
2. Tell Claude what you want in plain English. For example:
   *"On the Team page, update Max's bio to: …"* or *"Add a new operating partner, Sarah Lee, with this
   bio and this photo."*
3. Claude makes the change and opens a **pull request** (a proposed change, not yet live).
   It will give you a link.
4. On the pull request page, wait about a minute for Netlify to post a **Deploy Preview** link.
   Click it: that's exactly what the site will look like with your change.
5. Looks right? Click the green **Merge pull request** button, then **Confirm merge**.
   The live site updates within about a minute.
   Not right? Tell Claude what to fix; the preview refreshes on its own.

Nothing is public until you click Merge.

## How to undo a change

**Quickest:** log in to Netlify → the site → **Deploys** → click the last good deploy →
**Publish deploy**. The site rolls back instantly. Then ask Claude to properly revert the change in
GitHub so the next update doesn't bring the problem back.

## Don't touch without Madeline

- **GoDaddy DNS settings.** Company email depends on records there.
- **Netlify domain settings** and `netlify.toml`.

## Who to call

Madeline Ryerson set this up and can help with anything here.
Logins for GitHub, Netlify and GoDaddy are in the firm's password manager, not in this repository.

## For Claude

See `CLAUDE.md` for how changes must be made.
