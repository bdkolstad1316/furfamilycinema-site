# Agent Readiness — Fur Family Cinema

**Starting score:** 1/13 checks passing (homepage only)
**After remediation:** 8/13 checks passing (5 intentionally skipped as N/A)

## What was added

| File | Location | Purpose |
|---|---|---|
| `robots.txt` | Document root | AI bot rules + Content Signals. Blocks training bots, allows answer engines and live-user browsing. |
| `llms.txt` | Document root | Machine-readable site summary for AI agents. Services, pricing, hours, contact, booking links. |
| `sitemap.xml` | Document root | XML sitemap for crawler discoverability. |
| `nginx.conf` | Document root (used by Dockerfile) | Adds `Link:` response headers pointing to sitemap, llms.txt, and robots.txt. |

## Dockerfile update required

The Dockerfile needs one line added to copy the nginx config. Update it to:

```dockerfile
FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY . /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

The only change is line 2: `COPY nginx.conf /etc/nginx/conf.d/default.conf`

## Intentionally skipped (N/A for brochure site)

- **MCP Server Card** — No agent-drivable actions (no search, no checkout, no forms the site owns)
- **Agent Skills index** — Same reason
- **OAuth metadata** — No authenticated APIs
- **API catalog** — No public API
- **Markdown content negotiation** — Requires server-side logic; nginx can't do this natively. llms.txt covers the use case.

## Verification

After deploying, run:

```bash
curl -sI https://furfamilycinema-site-production.up.railway.app | grep -i '^link:'
curl -s https://furfamilycinema-site-production.up.railway.app/robots.txt | head -5
curl -s https://furfamilycinema-site-production.up.railway.app/llms.txt | head -3
curl -s https://furfamilycinema-site-production.up.railway.app/sitemap.xml | head -5
```

Or paste the URL into [isitagentready.com](https://isitagentready.com) to get the Cloudflare score.

## When to revisit

If the client adds a booking API, search endpoint, or authenticated portal, come back and add MCP discovery + OAuth metadata.
