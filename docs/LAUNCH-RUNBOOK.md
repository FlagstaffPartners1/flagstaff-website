# Launch runbook (one-time setup)

Order matters. Steps marked 👤 need a person logged in; everything else Claude can do.

## 1. GitHub
1. 👤 In the `FlagstaffPartners1` organization: **New repository** → name `flagstaff-website` →
   **Public** → do NOT add a README, .gitignore or license (the repo must be empty) → Create.
2. Push this folder to it (Claude, from Madeline's Mac, once she's logged in to GitHub there).
3. 👤 Repo → Settings → **Rules → Rulesets** → New branch ruleset: target the default branch,
   enable **Require a pull request before merging** with **0 required approvals**, and
   **Block force pushes**. (0 approvals because the person asking Claude is also the approver.)
4. 👤 Org → People: invite Tony (Owner or Member with Write/Maintain on this repo).

## 2. Netlify
1. 👤 Netlify (logged in via the FlagstaffPartners1 GitHub account) → **Add new project → Import an
   existing project → GitHub** → authorize for the `FlagstaffPartners1` org → pick `flagstaff-website`.
2. Build settings: leave build command **empty**, publish directory `.` (netlify.toml sets this).
   Deploy.
3. Open the `*.netlify.app` URL and click through every page.
4. Check Site configuration → Build & deploy → **Deploy Previews** are on for pull requests.
5. Optional: rename the site (Site configuration → Change site name) to `flagstaff-partners`, so
   the URL is `flagstaff-partners.netlify.app`.

## 3. Domain (GoDaddy): only after step 2 looks right
1. 👤 Netlify → Domain management → **Add a domain** → `flagstaff-partners.com`. Choose to keep
   DNS at the current provider (**do NOT** pick "Set up Netlify DNS", which moves nameservers and
   would put email at risk). Netlify adds `www` automatically.
2. 👤 GoDaddy → My Products → flagstaff-partners.com → **DNS**. Screenshot the full record list first.
3. Turn off anything GoDaddy has pointing the domain at a parking page/Website Builder/forwarding
   (if "Forwarding" is set on the domain, delete it).
4. Edit **only** these records (see `dns-snapshot-2026-10-06.md`):
   - **A @**: delete both existing A records (76.223.105.230, 13.248.243.5) and add one A record,
     name `@`, value `75.2.60.5`, TTL 1 hour.
   - **CNAME www**: change value to `<site-name>.netlify.app`.
5. Leave every MX, TXT, and other CNAME record exactly as is. Never change nameservers.
6. Back in Netlify, wait for DNS to verify, then **HTTPS → Verify DNS / Provision certificate**
   (usually minutes, can take up to 24 h). Set primary domain to `flagstaff-partners.com` so
   www redirects to it.

## 4. Verify
- https://flagstaff-partners.com and https://www.flagstaff-partners.com both load with a padlock.
- Send an email to and from a @flagstaff-partners.com address; both should arrive.
- Paste the homepage URL into a LinkedIn/iMessage draft: preview card shows logo and title.

## 5. Tony's Claude setup
1. 👤 Tony accepts the GitHub org invite (his own GitHub login).
2. 👤 Tony opens **claude.ai/code**, connects GitHub, and grants access to
   `FlagstaffPartners1/flagstaff-website` (an org owner may need to approve the Claude GitHub app).
3. Practice run: ask Claude for a tiny change, open the Deploy Preview, merge it.
