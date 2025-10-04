# 🚀 GMI Handbók - Ein-Skipun Deployment

## Fljótlegasta leiðin (1 skipun!)

### Option 1: Wrangler CLI (RÁÐLAGT)

```bash
# 1. Install Wrangler (ef ekki þegar uppsett)
npm install -g wrangler

# 2. Login
wrangler login

# 3. Deploy!
cd /path/to/gmi-site
wrangler pages deploy public --project-name=gmi-handbook
```

**✅ BÚIÐ!** Síðan er live á `https://gmi-handbook.pages.dev`

---

## Option 2: Cloudflare Dashboard (Engin CLI)

1. **Download**
   - Hala niður `gmi-public-only.zip`

2. **Upload**
   - Far á: https://dash.cloudflare.com/58af5443cdcb04b408dd29002ced60df/workers-and-pages
   - Create → Pages → Upload assets
   - Drag ZIP file
   - Project name: `gmi-handbook`

3. **Deploy**
   - Smelltu "Deploy"
   - Bíddu 30-60 sek

**✅ BÚIÐ!**

---

## Custom Domain Setup

Eftir deployment:

```bash
# Í terminal:
wrangler pages deployment tail --project-name=gmi-handbook

# Eða í Dashboard:
# 1. Fara í Pages project
# 2. Custom domains → Add domain
# 3. Enter: gmi.eyjar.app
# 4. Save
```

DNS er sett upp automatically af Cloudflare!

---

## Verify

```bash
# Check deployment
curl -I https://gmi-handbook.pages.dev

# Eða opna í browser:
open https://gmi-handbook.pages.dev
```

---

## Troubleshooting

**"wrangler: command not found"**
```bash
npm install -g wrangler
# eða
brew install cloudflare-wrangler
```

**"Not logged in"**
```bash
wrangler login
# Opens browser fyrir authentication
```

**"404 Not Found"**
- Athuga að þú ert í réttri möppu
- Athuga að `public/` directory er til
- Athuga að `index.html` er í `public/`

---

## Full Automation Script

Eða nota automation script:

```bash
cd /path/to/gmi-site
chmod +x deploy.sh
./deploy.sh
```

Script gerir:
- ✅ Checks fyrir wrangler
- ✅ Installs ef vantar
- ✅ Logs inn automatically
- ✅ Deployar project
- ✅ Shows útkomuna

---

## Environment Variables

Fyrir CI/CD deployment:

```bash
export CLOUDFLARE_ACCOUNT_ID="58af5443cdcb04b408dd29002ced60df"
export CLOUDFLARE_API_TOKEN="your-api-token"

wrangler pages deploy public \
  --project-name=gmi-handbook \
  --branch=main
```

Get API token from:
https://dash.cloudflare.com/profile/api-tokens

---

**Allt tilbúið! Aðeins ein skipun til að deploy! 🎉**
