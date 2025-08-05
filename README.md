# 🚀 Vercel Auto Deploy

**One-click GitHub Actions workflow for automatic Vercel deployments. Perfect for open source projects!**

## ✨ What does this do?

- ✅ **External contributors push** → Automatic Vercel deployment
- ✅ **You push** → No deployment (you control manually)  
- ✅ **Pure deployment** → No build steps, just triggers Vercel
- ✅ **Works with any project** → Node.js, Python, Go, static sites, anything Vercel supports

## 🚀 Setup (2 minutes)

### 1. Get your Vercel hook URL
1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Your Project → **Settings** → **Git** → **Deploy Hooks**
3. **Create Hook** → Copy the URL
<img width="1885" height="942" alt="image" src="https://github.com/user-attachments/assets/bb3b05f0-e6d0-4e0e-a9cc-82b6f57417ba" />


### 2. Add to GitHub
1. Your repo → **Settings** → **Secrets and variables** → **Actions**
2. **New repository secret**:
   - Name: `VERCEL_DEPLOY_HOOK`
   - Value: Your hook URL

### 3. Add this file: `.github/workflows/deploy.yml`
```yaml
name: Auto Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to Vercel
        uses: Gourav2609/vercel-auto-deploy@v1
        with:
          exclude-authors: 'YOUR_GITHUB_USERNAME'
          vercel-deploy-hook: ${{ secrets.VERCEL_DEPLOY_HOOK }}
```

**Replace `YOUR_GITHUB_USERNAME` with your GitHub username.**

### 4. Done! 🎉

That's it! Now when anyone else pushes to main, it auto-deploys. When you push, it doesn't.

## 🔧 Options

Want to exclude more users? Add them to the `with:` section:

```yaml
with:
  exclude-authors: 'YOUR_USERNAME,github-actions[bot],dependabot[bot]'  # Skip these users
  vercel-deploy-hook: ${{ secrets.VERCEL_DEPLOY_HOOK }}
```

## 🛠️ Troubleshooting

**❌ "Input required and not supplied: vercel-deploy-hook"**
- Check you added the secret with exact name `VERCEL_DEPLOY_HOOK`

**❌ "Build failed"**
- This workflow only triggers deployment - if your Vercel build fails, check your Vercel dashboard

**❌ "Deployment not triggered"**
- Verify your username is in `exclude-authors`
- Confirm push was to `main` branch

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 📞 Need Help?

- 🐛 [Report Issues](https://github.com/Gourav2609/vercel-auto-deploy/issues)

---

**Made with ❤️ to make deployments easier**
