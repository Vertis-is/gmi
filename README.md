# 🏥 GMI Handbók + Heilsulykill Platform

**Professional Graded Motor Imagery (GMI) Handbook + Healthcare Resource Platform**

[![Cloudflare Workers](https://img.shields.io/badge/Cloudflare-Workers-orange)](https://workers.cloudflare.com/)
[![React](https://img.shields.io/badge/React-18-blue)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-blue)](https://www.typescriptlang.org/)
[![Durable Objects](https://img.shields.io/badge/Durable-Objects-orange)](https://developers.cloudflare.com/durable-objects/)

**Live Site**: [gmi.eyjar.app](https://gmi.eyjar.app) *(coming soon)*  
**Repository**: [github.com/Vertis-is/gmi](https://github.com/Vertis-is/gmi)

---

## 📖 About This Project

This is a comprehensive healthcare platform combining:

1. **GMI Handbók** - Professional 5-step Graded Motor Imagery handbook for Icelandic therapists treating CRPS (Complex Regional Pain Syndrome)
2. **Heilsulykill.is Content** - Migrated health resources, courses, and support services
3. **Real-time Chat** - Cloudflare Durable Objects powered chat for professional collaboration

### Target Users

- **Primary**: Íslenskir iðjuþjálfar (Icelandic occupational therapists)
- **Secondary**: Healthcare professionals (physicians, physical therapists, psychologists)
- **Tertiary**: Patients, caregivers, and families

---

## ✨ Key Features

### GMI Handbook
- ✅ 5 comprehensive pages (overview + 4 treatment steps)
- ✅ Evidence-based protocols from NOI Group research
- ✅ Professional Icelandic medical terminology
- ✅ Step-by-step patient instructions
- ✅ Troubleshooting guides
- ✅ Equipment purchasing information

### Heilsulykill Integration
- ✅ Migrated course catalog
- ✅ Event listings (námskeið, viðburðir)
- ✅ Resource directory (úrræði, stofnanir)
- ✅ Support groups (samtök, stuðningshópar)

### Real-time Collaboration
- ✅ Durable Objects chat rooms per GMI step
- ✅ Professional discussion channels
- ✅ Patient support groups
- ✅ Persistent message history

---

## 🛠️ Technical Stack

### Frontend
- **React 18** with TypeScript
- **React Router 7** for navigation
- **PartySocket** for WebSocket connections
- **Pico CSS** for styling

### Backend
- **Cloudflare Workers** - Serverless compute
- **Durable Objects** - Stateful real-time chat
- **R2 Storage** - Asset hosting
- **KV Storage** - Configuration data

### Development
- **esbuild** - Fast bundling
- **Wrangler** - Cloudflare CLI
- **Docker** - Local WordPress development
- **Apify** - Web scraping for migration

---

## 📂 Project Structure

```
C:\git\gmi\
├── src/
│   ├── client/                  # React frontend
│   │   ├── index.tsx           # Entry point
│   │   ├── components/
│   │   │   ├── GMI/            # GMI handbook components
│   │   │   │   ├── Forsida.tsx
│   │   │   │   ├── Skref1.tsx  # Laterality Recognition
│   │   │   │   ├── Skref2.tsx  # Motor Imagery
│   │   │   │   ├── Skref3.tsx  # Mirror Therapy
│   │   │   │   └── Skref4.tsx  # Desensitization
│   │   │   ├── Chat/           # Chat components
│   │   │   │   ├── ChatWindow.tsx
│   │   │   │   └── ChatWidget.tsx
│   │   │   └── Heilsulykill/   # Migrated content
│   │   │       ├── CourseList.tsx
│   │   │       └── CourseDetail.tsx
│   │   └── routes.tsx
│   ├── server/                  # Cloudflare Workers
│   │   ├── index.ts            # Main worker
│   │   └── chat.ts             # Durable Objects chat
│   └── shared.ts                # Shared types
├── public/                      # Static assets
│   ├── index.html
│   ├── assets/
│   └── heilsulykill/           # Scraped content
├── docs/                        # Documentation
│   ├── HEILSULYKILL-MIGRATION-PLAN.md
│   ├── DEPLOYMENT.md
│   └── claude-log.md
├── index.html                   # Original GMI HTML
├── skref1-4.html               # Original GMI steps
├── package.json
├── wrangler.json
├── tsconfig.json
└── TODO.md
```

---

## 🚀 Quick Start

### Prerequisites
```bash
# Install Node.js 18+
node --version

# Install Wrangler CLI
npm install -g wrangler

# Install Docker (for local WordPress)
docker --version
```

### Development Setup

```bash
# Clone repository
git clone https://github.com/Vertis-is/gmi.git
cd gmi

# Install dependencies
npm install

# Start development server
npm run dev

# Open browser
# http://localhost:8787
```

### Build & Deploy

```bash
# Build production bundle
npm run build

# Deploy to Cloudflare
wrangler deploy

# Setup custom domain
wrangler domains add gmi.eyjar.app
```

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [TODO.md](./TODO.md) | Complete task list and progress tracking |
| [HEILSULYKILL-MIGRATION-PLAN.md](./HEILSULYKILL-MIGRATION-PLAN.md) | Migration strategy and implementation |
| [claude-log.md](./claude-log.md) | AI-assisted development activity log |
| [DEPLOYMENT.md](./DEPLOYMENT.md) | Cloudflare deployment guide |

---

## 🔄 Development Workflow

### Phase 1: GMI HTML Pages ✅ COMPLETE
- [x] Create 5 HTML pages with Pico CSS
- [x] Professional Icelandic content
- [x] Evidence-based protocols

### Phase 2: Heilsulykill Scraping 🔄 IN PROGRESS
- [ ] Run Apify Website Content Crawler
- [ ] Download and organize data
- [ ] Map content structure

### Phase 3: React Integration 🔄 IN PROGRESS
- [ ] Convert HTML to React components
- [ ] Setup routing
- [ ] Implement navigation

### Phase 4: Chat Integration ⏸️ PENDING
- [ ] Integrate chat widget
- [ ] Create room structure
- [ ] Test real-time messaging

### Phase 5: WordPress Local ⏸️ PENDING
- [ ] Docker setup
- [ ] Content import
- [ ] Testing

### Phase 6: Production Deploy ⏸️ PENDING
- [ ] Cloudflare Workers deployment
- [ ] DNS configuration
- [ ] Go live!

---

## 🎯 Routes

| Route | Component | Description |
|-------|-----------|-------------|
| `/` | GMI Forsíða | Overview and introduction |
| `/gmi/skref1` | Laterality | Laterality Recognition training |
| `/gmi/skref2` | Motor Imagery | Explicit motor imagery exercises |
| `/gmi/skref3` | Mirror Therapy | Mirror therapy protocols |
| `/gmi/skref4` | Desensitization | Texture desensitization program |
| `/namskeið` | Courses | Heilsulykill course catalog |
| `/úrræði` | Resources | Support resources directory |
| `/chat/:room` | Chat | Real-time discussion rooms |

---

## 📊 Evidence Base

The GMI handbook is based on:

- **Moseley, G.L. (2004, 2006)** - Original GMI research
- **Bowering, K.J., et al. (2013)** - Systematic review
- **Flor, H., et al. (2006)** - Cortical reorganization
- **NOI Group protocols** - Clinical guidelines
- **Ramachandran, V.S. (1996)** - Mirror therapy

---

## 🔐 Environment Variables

```bash
# Required for production
CLOUDFLARE_API_TOKEN=your-token
CLOUDFLARE_ACCOUNT_ID=your-account-id

# Optional
APIFY_API_TOKEN=your-apify-token
```

---

## 🤝 Contributing

This is a proprietary project developed by Vertis for Icelandic healthcare.

For inquiries:
- **Email**: omar@omaromar.net
- **Company**: https://vertis.is

---

## 📄 License

© 2025 Vertis.is. All rights reserved.

This is proprietary healthcare content developed for the Icelandic healthcare system.

---

## 👥 Team

**Development**: Omar @ Vertis.is  
**Client**: Reykjavik City Healthcare  
**Content**: Based on NOI Group protocols  
**Innovation**: Hrefna Óskarsdóttir (Desensitization integration)

---

## 🔗 Links

- **Live Site**: [gmi.eyjar.app](https://gmi.eyjar.app) *(coming soon)*
- **Source**: [Heilsulykill.is](https://heilsulykill.is)
- **Cloudflare**: [Dashboard](https://dash.cloudflare.com)
- **Apify**: [Console](https://console.apify.com)

---

## 📅 Version History

### v1.0.0 - 2025-10-04
- ✅ Initial GMI HTML pages
- ✅ Cloudflare template integration
- ✅ Project structure
- 🔄 Heilsulykill migration in progress
- 🔄 React conversion in progress

---

**GMI + Heilsulykill Platform v1.0**  
*Professional healthcare resource platform for Iceland*  
October 2025
