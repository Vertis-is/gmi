# 🚀 GMI Handbók - Quick Start Guide

## Hratt Yfirlit

**Vefsíðan er tilbúin!** Þú hefur þrjá möguleika til að setja hana upp:

## ⚡ Fljótlegasta leiðin (5 mínútur)

### Cloudflare Pages Direct Upload

1. **Download skrár**
   - Halaðu niður `gmi-public-only.zip`

2. **Opna Cloudflare Dashboard**
   - Farðu á: https://dash.cloudflare.com/58af5443cdcb04b408dd29002ced60df/workers-and-pages
   - (Eða bara dash.cloudflare.com og veldu "Workers & Pages")

3. **Create New Pages Project**
   - Smelltu á "Create application"
   - Veldu "Pages" tab
   - Veldu "Upload assets"

4. **Upload ZIP**
   - Dragðu `gmi-public-only.zip` inn
   - EÐA unzip það og dragðu öll HTML skrárnar
   - Project name: `gmi-handbook`
   - Smelltu á "Deploy site"

5. **Bíddu 30-60 sekúndur**
   - Deployment klárast
   - Þú færð link: `https://gmi-handbook.pages.dev`

6. **Set up Custom Domain**
   - Í Pages project, farðu í "Custom domains"
   - Add: `gmi.eyjar.app`
   - Cloudflare setur DNS automatically

**BÚIÐ! ✅**

## 📦 Skrár sem þú hefur

```
gmi-handbook-complete.zip  (36KB)
├── Öll source files
├── DEPLOYMENT.md (full instructions)
├── README.md (documentation)
└── public/ (HTML files)

gmi-public-only.zip (29KB)
└── Bara HTML skrárnar (fyrir direct upload)
```

## 🌐 Aðgangur

Eftir deployment:

- **Pages.dev subdomain:** https://gmi-handbook.pages.dev
- **Custom domain:** https://gmi.eyjar.app (eftir DNS setup)

## 📱 Test Checklist

- [ ] Opna forsíðuna
- [ ] Test öll 5 skrefin (navigation menu)
- [ ] Test á mobile (responsive design)
- [ ] Athuga að CSS virkar (Pico CSS)

## 🔧 Ef eitthvað fer úrskeiðis

### "Ég sé bara hvíta síðu"
- Refresh síðuna (Ctrl+F5)
- Check browser console fyrir errors

### "404 Not Found"
- Gakktu úr skugga um að `index.html` sé í root
- Ekki setja files í subfolder

### "CSS virkar ekki"
- Check nettenging
- CDN gæti verið blocked - try annað network

### "gmi.eyjar.app virkar ekki"
- DNS tekur 5-30 mínútur að propagate
- Athugaðu DNS settings í Cloudflare

## 📞 Aðstoð

Ef þú þarft hjálp:

1. Skoðaðu `DEPLOYMENT.md` fyrir detailed instructions
2. Cloudflare Docs: https://developers.cloudflare.com/pages/
3. Email: omar@omaromar.net

## 🎉 Næstu skref

Eftir deployment:

1. ✅ Share með iðjuþjálfum
2. ✅ Gather feedback
3. ✅ Bæta við raunverulegum myndum (placeholders núna)
4. ✅ Consider analytics setup

---

**GMI Handbók v1.0** | Þróað fyrir Vertis | október 2025
