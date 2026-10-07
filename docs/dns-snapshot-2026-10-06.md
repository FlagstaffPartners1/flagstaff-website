# DNS snapshot: flagstaff-partners.com (taken 2026-10-06, before website launch)

Read from public DNS. Registrar and DNS host: **GoDaddy** (nameservers ns69/ns70.domaincontrol.com).
If anything at GoDaddy is changed by mistake, restore it to exactly this.

## Records the website launch CHANGES (only these two)

| Type | Name | Value before launch | Value after launch |
|---|---|---|---|
| A | @ | 76.223.105.230 **and** 13.248.243.5 (GoDaddy parking/builder) | 75.2.60.5 (Netlify), single record |
| CNAME | www | flagstaff-partners.com | `<your-site>.netlify.app` |

## Records that must NOT be touched (company email, Microsoft 365, verifications)

| Type | Name | Value | Purpose |
|---|---|---|---|
| MX | @ | 0 flagstaffpartners-com02c.mail.protection.outlook.com | Email delivery |
| TXT | @ | v=spf1 include:spf.protection.outlook.com -all | Email anti-spoofing (SPF) |
| TXT | @ | MS=ms65272421 | Microsoft 365 domain verification |
| TXT | @ | google-site-verification=aQW9MMIIWEwa-BIHnmPnfah2XSURsr9GuKYBMc0ExeQ | Google verification |
| TXT | @ | anthropic-domain-verification-majnjm=JDF4CR9XSx2b2Hvz0ZhSLVz0b | Anthropic (Claude) verification |
| TXT | _dmarc | v=DMARC1; p=quarantine; rua=mailto:dmarc@flagstaff-partners.com | Email policy (DMARC) |
| CNAME | selector1._domainkey | selector1-flagstaffpartners-com02c._domainkey.flagstaffpartnersus.a-v1.dkim.mail.microsoft | Email signing (DKIM) |
| CNAME | selector2._domainkey | selector2-flagstaffpartners-com02c._domainkey.flagstaffpartnersus.a-v1.dkim.mail.microsoft | Email signing (DKIM) |
| CNAME | autodiscover | autodiscover.outlook.com | Outlook auto-setup |
| CNAME | enterpriseregistration | enterpriseregistration.windows.net | Microsoft device registration |
| CNAME | enterpriseenrollment | enterpriseenrollment-s.manage.microsoft.com | Microsoft device management |
| CNAME | _domainconnect | _domainconnect.gd.domaincontrol.com | GoDaddy internal |
| NS | @ | ns69.domaincontrol.com, ns70.domaincontrol.com | **Never change nameservers** |

Note: a public lookup can't list every record (e.g. SRV records under unusual names). Before
editing, take a screenshot of the full record list in GoDaddy's DNS page as a second backup.
