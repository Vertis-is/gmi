# GMI Handbók - Deployment Leiðbeiningar

## 📦 Hvað er í þessum pakka

Þessi pakki inniheldur alla nauðsynlega skrár fyrir GMI (Graded Motor Imagery) handbókina:

```
gmi-site/
├── public/
│   ├── index.html          # Forsíða með yfirliti
│   ├── skref1.html          # Laterality Recognition
│   ├── skref2.html          # Explicit Motor Imagery
│   ├── skref3.html          # Mirror Therapy
│   └── skref4.html          # Desensitization
├── wrangler.toml            # Cloudflare Worker config
├── src/
│   └── index.js             # Worker script (optional)
└── DEPLOYMENT.md            # Þessi skrá
```

## 🚀 Deployment á Cloudflare Pages (RÁÐLAGT)

### Aðferð 1: Direct Upload (Fljótlegast)

1. **Innskrá á Cloudflare Dashboard**
   - Far á: https://dash.cloudflare.com/
   - Veldu þinn account

2. **Opna Workers & Pages**
   - Í vinstri menu, veldu "Workers & Pages"
   - Smelltu á "Create application"

3. **Veldu Pages**
   - Veldu "Pages" tab
   - Veldu "Upload assets"

4. **Upload skrárnar**
   - Dragðu alla skrárnar úr `public/` möppunni
   - EÐA zip-aðu `public/` möppuna og drag

u ZIP skrána
   - Smelltu á "Deploy site"

5. **Nefna projectið**
   - Project name: `gmi-handbook` (eða eitthvað annað)
   - Smelltu á "Save and Deploy"

6. **Bíddu eftir deployment**
   - Þetta tekur 30-60 sekúndur
   - Þú færð `.pages.dev` subdomain sjálfkrafa

### Aðferð 2: Git Integration

1. **Búa til GitHub repository**
   - Far á https://github.com/new
   - Nefndu það t.d. "gmi-handbook"
   - Create repository

2. **Upload skrár til GitHub**
   ```bash
   cd /path/to/gmi-site/public
   git init
   git add .
   git commit -m "Initial commit - GMI Handbók"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/gmi-handbook.git
   git push -u origin main
   ```

3. **Tengja við Cloudflare Pages**
   - Í Cloudflare Dashboard: Workers & Pages → Create → Pages
   - Veldu "Connect to Git"
   - Authorize GitHub
   - Veldu repository-ið þitt
   - Build settings:
     - Build command: (skildu eftir tómt)
     - Build output directory: `/`
     - Root directory: (skildu eftir tómt)
   - Save and Deploy

## 🌐 Custom Domain Setup: gmi.eyjar.app

Eftir að deployment er lokið, þarft þú að setja upp custom domain:

### Skref 1: Bæta við Custom Domain

1. **Í Cloudflare Pages**
   - Far á þitt Pages project
   - Veldu "Custom domains" tab
   - Smelltu á "Set up a custom domain"

2. **Enter domain**
   - Sláðu inn: `gmi.eyjar.app`
   - Smelltu á "Continue"

### Skref 2: DNS Configuration

Ef `eyjar.app` er á Cloudflare (líklega):

1. **Far í DNS settings**
   - Workers & Pages → Custom Domains → Set up domain
   - Cloudflare mun automatically add DNS record

2. **Manual DNS (ef þarf)**
   - Far í "DNS" fyrir `eyjar.app` domain
   - Bæta við CNAME record:
     ```
     Type: CNAME
     Name: gmi
     Target: gmi-handbook.pages.dev
     Proxy status: Proxied (orange cloud)
     ```

3. **Bíddu eftir propagation**
   - DNS propagation getur tekið 5-10 mínútur
   - Stundum allt að 24 klukkustundir

### Skref 3: SSL Certificate

- Cloudflare veitir automatic SSL/TLS certificate
- Það activates sjálfkrafa eftir DNS setup
- https://gmi.eyjar.app verður virkt

## ✅ Verification Checklist

Eftir deployment, athugaðu:

- [ ] https://YOUR-PROJECT.pages.dev virkar
- [ ] https://gmi.eyjar.app virkar (eftir DNS setup)
- [ ] Allar 5 síður virka:
  - [ ] / (index.html)
  - [ ] /skref1.html
  - [ ] /skref2.html
  - [ ] /skref3.html
  - [ ] /skref4.html
- [ ] Navigation menu virkar
- [ ] Pico CSS loads correctly
- [ ] Google Fonts loads
- [ ] Responsive design virkar á mobile

## 🔧 Troubleshooting

### "404 Not Found" á pages.dev

- **Orsök:** index.html er ekki í root directory
- **Lausn:** Gakktu úr skugga um að allar .html skrár séu í root af deployment

### "DNS_PROBE_FINISHED_NXDOMAIN" fyrir gmi.eyjar.app

- **Orsök:** DNS hefur ekki propagated ennþá
- **Lausn:** 
  - Athugaðu DNS records í Cloudflare Dashboard
  - Bíddu 10-30 mínútur
  - Clear browser cache og DNS cache

### CSS virkar ekki

- **Orsök:** CDN links blocked eða slow
- **Lausn:** 
  - Athugaðu browser console fyrir errors
  - Verify Pico CSS CDN er accessible
  - Check Content Security Policy settings

### Myndir/placeholders eru missing

- **Orsök:** Þær voru ekki included í deployment
- **Lausn:** Þetta er normalt - placeholders eru í HTML, raunverulegar myndir verða bætt við síðar

## 📊 Performance Optimization

Cloudflare Pages automatically veitir:

- ✅ Global CDN
- ✅ HTTP/3 support
- ✅ Brotli compression
- ✅ Smart caching
- ✅ DDoS protection
- ✅ Analytics

## 🔄 Updates & Maintenance

### Að uppfæra efni:

**Með Direct Upload:**
1. Edit HTML skrár locally
2. Far aftur á Pages project
3. "Create new deployment"
4. Upload updated files

**Með Git:**
1. Edit HTML skrár locally
2. Commit og push til GitHub:
   ```bash
   git add .
   git commit -m "Update GMI content"
   git push
   ```
3. Cloudflare automatically rebuilds

### Version Control:

- Hver deployment er saved
- Þú getur rolled back til previous versions
- Deployment history er available í dashboard

## 📧 Support

Ef þú lendir í vandræðum:

1. **Cloudflare Documentation:** https://developers.cloudflare.com/pages/
2. **Cloudflare Community:** https://community.cloudflare.com/
3. **Omar:** omar@omaromar.net
4. **Vertis:** https://vertis.is

## 🎉 Næstu skref

Eftir deployment:

1. **Test thoroughly:** Farðu í gegnum allar síður
2. **Share with team:** Deildu link með íðjuþjálfum
3. **Gather feedback:** Safna athugasemdum og suggestions
4. **Add images:** Bættu við raunverulegum myndum í placeholders
5. **Analytics:** Set up Cloudflare Web Analytics ef þú vilt track usage

---

**GMI Handbók v1.0**  
Þróað fyrir Vertis og íslenska iðjuþjálfa  
Október 2025
