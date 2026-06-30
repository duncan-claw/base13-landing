# BASE13 Deployment

## Current deploy

- Repository: https://github.com/duncan-claw/base13-landing
- Hosting: GitHub Pages
- Pages source: `main` branch, repository root
- Canonical domain: `base13.ai`
- Contact form backend: `https://postie.duncanclaw.ai/submissions`
- Contact recipient: `mark@gr8ful.dev`

## Primary domain DNS

Set `base13.ai` DNS at the registrar/DNS host to GitHub Pages.

A records for apex `base13.ai`:

```text
@  A  185.199.108.153
@  A  185.199.109.153
@  A  185.199.110.153
@  A  185.199.111.153
```

Optional IPv6 records:

```text
@  AAAA  2606:50c0:8000::153
@  AAAA  2606:50c0:8001::153
@  AAAA  2606:50c0:8002::153
@  AAAA  2606:50c0:8003::153
```

`www` record:

```text
www  CNAME  duncan-claw.github.io
```

Remove the current GoDaddy parking A records before adding the GitHub Pages A records.

## Redirect domains

Redirect these domains permanently to `https://base13.ai`:

- `base13.co`
- `base13.io`
- `base13.com.au`
- `www.base13.ai`
- optionally all `www` variants for the redirect domains

Preferred implementation if/when Cloudflare access is available:

1. Move all four zones to Cloudflare nameservers.
2. Host `base13.ai` with Cloudflare Pages or keep GitHub Pages and proxy/redirect through Cloudflare.
3. Add bulk redirects/page rules from the secondary domains to `https://base13.ai/$1`.

If staying at GoDaddy DNS, use GoDaddy domain forwarding for the secondary domains if HTTPS forwarding is supported cleanly.

## Postie allowed origins

Postie Website is currently configured for:

- `https://base13.ai`
- `http://base13.ai`
- `https://www.base13.ai`
- `http://localhost:4173`
- `http://127.0.0.1:4173`

If a secondary domain ever serves the form directly rather than redirecting first, add that origin to Postie before launch.

## Live test checklist

After DNS propagates:

1. Open `https://base13.ai`.
2. Confirm SSL is valid.
3. Submit a real contact form test.
4. Confirm success state on the site.
5. Confirm message delivery to `mark@gr8ful.dev`.
6. Confirm secondary domains 301/302 redirect to `https://base13.ai`.
