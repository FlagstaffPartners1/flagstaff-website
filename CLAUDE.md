# Instructions for Claude: Flagstaff Partners website

You are helping a partner at Flagstaff Partners (a private investment firm in Denver) update the
firm's public website, https://flagstaff-partners.com. **The person asking is not a web developer.**
They will review your change by clicking a preview link and then approving it. Optimize for that.

## How every change must be made (non-negotiable)

1. **Never commit to `main`.** `main` is the live website: anything merged there is public within
   about a minute. Always create a new branch named for the change (e.g. `update-team-bios`).
2. **Open a pull request** for every change, even a one-word fix. Title it in plain English
   ("Add Sarah Lee to the Team page"), not developer shorthand.
3. In the pull request description, write for a non-technical reader:
   - **What changed**, page by page, in plain English.
   - **What to check** on the preview (e.g. "Scroll to Operating Partners on the Team page").
   - Anything you were unsure about or assumed.
4. Netlify automatically posts a **Deploy Preview** link on the pull request about a minute after
   it opens. Tell the user to click it, check the page(s), and then click **Merge** if it looks
   right. If they want changes, update the same branch; the preview refreshes automatically.
5. Do not merge the pull request yourself unless the user explicitly tells you to.
6. Before you finish, re-read every file you changed and check the "Repeated on every page" list
   below.

## Ask before you…

- Change wording about the firm's track record, numbers, or investment strategy (stats on the
  homepage, "Approach", "About"). These are partner-approved statements; confirm the exact text.
- Add, remove, or change any person on the Team page, or any email address.
- Delete a page, rename a page's file, or change the site's look (colors, fonts, layout).
- Anything involving the domain, DNS, email, GoDaddy, or Netlify settings. **Do not attempt these.**
  Tell the user to contact Madeline Ryerson, who set up the site. The firm's email runs on the same
  domain and a DNS mistake can break company email.

## How the site is built

Plain HTML and CSS. No framework, no build step, nothing to install. Netlify publishes the repo
folder exactly as it is.

| File | Page |
|---|---|
| `index.html` | Home (hero video, stats, approach summary) |
| `about.html` | About |
| `team.html` | Team (partner names, roles, bios, emails) |
| `approach.html` | Approach |
| `responsibility.html` | Responsibility |
| `contact.html` | Contact (emails, office address) |
| `404.html` | "Page not found" page (uses `/`-prefixed paths on purpose so it works at any URL) |
| `styles.css` | All styling for every page |
| `assets/` | Logos, favicons, `photos/`, `video/` |
| `netlify.toml` | Hosting settings (headers, caching). Don't change without asking. |
| `sitemap.xml`, `robots.txt` | For search engines. Update `sitemap.xml` if a page is added/removed. |

### Repeated on every page: change ALL copies

There are no shared templates. Each of the 7 HTML files carries its own copy of:

- **Top navigation** (`<header class="site-nav">`) and **mobile menu** (`<div class="mobile-menu">`).
  The current page's mobile-menu link has `aria-current="page"`.
- **Footer** (`<footer class="site-footer">`): links, address, LinkedIn.
- **The `<head>` block**: fonts, favicon, stylesheet link.
- **The JavaScript** at the bottom of the page (GSAP animations + Lenis smooth scrolling). It is
  identical on every page. If you change it, change it identically everywhere.

If you change one of these, make the same change in all 7 files (including `404.html`, where links
start with `/`). Search the repo afterward to confirm nothing was missed.

### Patterns to follow

- Animations are driven by attributes: `data-reveal` (fade in on scroll), `data-lines`
  (headline line-by-line reveal), `data-count` (number count-up on homepage stats). Reuse them
  on new elements that sit alongside similar ones.
- Each page has `<title>`, `<meta name="description">`, `og:` tags and a canonical URL of the
  form `https://flagstaff-partners.com/<page>.html`. Keep these accurate if page content changes.
- Email addresses are shown with a non-breaking hyphen (`flagstaff&#8209;partners.com`) so they
  don't wrap. Keep the `mailto:` link using a normal hyphen.
- Comments marked `[CONFIRM]` are content still awaiting partner sign-off. Don't remove them
  unless the user confirms the item.

### Images and video

- Photos live in `assets/photos/`, video in `assets/video/`. Never link to images on other websites.
- Keep files small: photos ≤ ~2400 px wide and under ~1 MB (JPG, quality ~80). Provide a smaller
  version for phones and list both in `srcset`, as the existing images do.
- Headshots or new photos the user provides: resize them before adding. Use descriptive file names
  (`team-sarah-lee.jpg`) and always write meaningful `alt` text.
- The homepage hero video (`assets/video/hero.mp4`) must stay under ~10 MB, with no audio track.

## Checking your work

You can't see the live preview yourself unless you have a browser tool, so before opening the PR:
- Confirm every link and image path you touched points to a file that exists in the repo.
- Confirm HTML tags you added are closed and the page structure matches neighbouring sections.
- If you have a way to run a local web server and view the page, do it and look at it on a narrow
  (phone-width) and wide window.
