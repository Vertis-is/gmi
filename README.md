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
├── src/                         # Active development code
│   ├── client/                  # React frontend
│   │   ├── index.tsx           # Entry point
│   │   └── components/         # React components
│   ├── server/                  # Cloudflare Workers
│   │   ├── index.ts            # Main worker + Durable Objects
│   │   └── tsconfig.json
│   └── shared.ts                # Shared TypeScript types
├── public/                      # Static assets
│   ├── index.html              # Chat app HTML
│   ├── css/                    # Skeleton CSS framework
│   ├── styles.css              # Custom styles
│   └── favicon.ico
├── old/                         # Archived legacy content
│   ├── index.html              # Original GMI HTML pages
│   ├── skref1-4.html          # Original GMI steps
│   ├── TODO.md                # Historical planning docs
│   ├── claude-log.md          # Development logs
│   └── *.md                   # Other archived documentation
├── CLAUDE.md                    # AI coding guidance (active)
├── CLEANUP-ANALYSIS.md          # This cleanup process
├── DEPLOYMENT.md                # Deployment instructions (active)
├── README.md                    # This file
├── package.json                 # NPM dependencies
├── wrangler.json                # Cloudflare configuration
└── tsconfig.json                # TypeScript config
```

**Note**: Legacy HTML files and historical documentation have been moved to `old/` for reference. Active development focuses on the React/Cloudflare Workers implementation in `src/`.

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

| Document | Description | Location |
|----------|-------------|----------|
| [CLAUDE.md](./CLAUDE.md) | AI coding guidance and project overview | Active |
| [DEPLOYMENT.md](./DEPLOYMENT.md) | Cloudflare deployment guide (Icelandic) | Active |
| [CLEANUP-ANALYSIS.md](./CLEANUP-ANALYSIS.md) | Project cleanup and file organization | Active |
| [TODO.md](./old/TODO.md) | Complete task list and progress tracking | Archived |
| [HEILSULYKILL-MIGRATION-PLAN.md](./old/HEILSULYKILL-MIGRATION-PLAN.md) | Migration strategy | Archived |
| [claude-log.md](./old/claude-log.md) | AI development activity log | Archived |

**Active Documentation**: Files in root directory are maintained and current.  
**Archived Documentation**: Historical files in `old/` directory for reference.

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
