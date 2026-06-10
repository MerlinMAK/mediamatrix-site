# Media Matrix — marketing site

Static site. No build step. `index.html` + `start.html`.

## Deploy (GitHub Pages)

```bash
gh repo create mediamatrix-site --public --source=. --push
gh api repos/{owner}/mediamatrix-site/pages -X POST -f build_type=workflow 2>/dev/null || true
```

Or via UI: repo → Settings → Pages → Source: "Deploy from a branch" → main / root.

Live at: https://<username>.github.io/mediamatrix-site/

## Custom domain

1. Add file `CNAME` containing your domain (e.g. `mediamatrix.com`) to repo root, or set it in Settings → Pages → Custom domain.
2. Configure DNS (see below), enable "Enforce HTTPS" once cert issues (~15 min).

### DNS — apex domain (mediamatrix.com)
A records:
- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

AAAA (optional, IPv6):
- 2606:50c0:8000::153
- 2606:50c0:8001::153
- 2606:50c0:8002::153
- 2606:50c0:8003::153

### DNS — www
CNAME: www → <username>.github.io
