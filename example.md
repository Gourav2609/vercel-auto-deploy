# ✨ Real Example

This is how I use it on my documentation site [lighthooks.com](https://lighthooks.com):

## My workflow file: `.github/workflows/deploy.yml`

```yaml
name: Auto Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    uses: Gourav2609/vercel-auto-deploy/.github/workflows/auto-deploy.yml@v1
    with:
      exclude-authors: 'Gourav2609,github-actions[bot]'
    secrets:
      VERCEL_DEPLOY_HOOK: ${{ secrets.VERCEL_DEPLOY_HOOK }}
```

## What happens:
- ✅ When I push → Nothing (I control deployments manually)
- ✅ When contributors push → Auto-deploy to Vercel
- ✅ Simple trigger → Vercel handles all the building

Perfect for any project - documentation sites, Next.js apps, static sites, anything!
