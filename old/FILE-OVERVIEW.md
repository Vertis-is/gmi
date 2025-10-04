# GMI Project - Complete File Overview

**Generated**: 2025-10-04
**Purpose**: Document all files before moving to old/ directory

---

## 📁 Root Directory Files

### Configuration Files

#### `package.json`
- **Type**: NPM configuration
- **Purpose**: Defines project dependencies and scripts
- **Contains**:
  - React, PartyKit, Durable Objects dependencies
  - Build scripts (check, deploy, dev)
  - Project metadata for chat app template

#### `package-lock.json`
- **Type**: NPM lock file
- **Purpose**: Locks dependency versions for consistent installs
- **Size**: 73KB

#### `wrangler.json`
- **Type**: Cloudflare Workers configuration
- **Purpose**: Defines deployment settings for Cloudflare Workers
- **Contains**:
  - Durable Objects bindings for Chat class
  - Asset directory configuration (./public)
  - Build commands for esbuild
  - SQL migrations for chat messages

#### `tsconfig.json`
- **Type**: TypeScript configuration
- **Purpose**: TypeScript compiler settings
- **Size**: 323 bytes

#### `.gitignore`
- **Type**: Git ignore rules
- **Purpose**: Specifies files/folders to exclude from git
- **Size**: 3KB

---

## 📄 Documentation Files

### Main Documentation

#### `README.md`
- **Type**: Project documentation
- **Purpose**: Main project overview for GMI Handbók
- **Contains**:
  - Project description (GMI Handbook for CRPS)
  - 5-page handbook structure overview
  - Target audience (Icelandic occupational therapists)
  - Technical stack (HTML5, Pico CSS, Cloudflare Pages)
  - Evidence base and research citations
  - Deployment instructions
  - Credits and license information
- **Size**: 4.9KB

### Deployment Documentation

#### `DEPLOYMENT.md`
- **Type**: Deployment guide
- **Purpose**: Step-by-step Cloudflare deployment instructions
- **Contains**:
  - Cloudflare Pages direct upload method
  - Git integration method
  - Custom domain setup (gmi.eyjar.app)
  - DNS configuration
  - SSL certificate setup
  - Troubleshooting guide
- **Size**: 6KB

#### `MCP-DEPLOYMENT-GUIDE.md`
- **Type**: MCP-specific deployment guide
- **Purpose**: Model Context Protocol deployment instructions
- **Size**: 4KB

#### `MCP-FINAL-DEPLOYMENT.md`
- **Type**: Final MCP deployment documentation
- **Purpose**: Complete MCP deployment checklist
- **Size**: 6.1KB

#### `ONE-COMMAND-DEPLOY.md`
- **Type**: Quick deployment guide
- **Purpose**: Simplified one-command deployment instructions
- **Size**: 2.2KB

#### `QUICK-START.md`
- **Type**: Quick start guide
- **Purpose**: 5-minute setup instructions
- **Size**: 2.5KB

### Project Planning

#### `PROJECT-SUMMARY.md`
- **Type**: Project summary
- **Purpose**: Complete project overview and deliverables
- **Contains**:
  - What was built (5-page GMI handbook)
  - Page descriptions and content breakdown
  - Design features and technical stack
  - Deployment options
  - Statistics (3000+ lines, 107KB content)
  - Credits and acknowledgments
- **Size**: 9KB

#### `TODO.md`
- **Type**: Task list and project plan
- **Purpose**: Comprehensive project roadmap
- **Contains**:
  - Project goals and status
  - 6 phases: GMI pages, heilsulykill scraping, React integration, chat, WordPress, deployment
  - Timeline and milestones
  - Technical debt tracking
  - Known issues and future enhancements
- **Size**: 9.4KB

#### `HEILSULYKILL-MIGRATION-PLAN.md`
- **Type**: Migration strategy
- **Purpose**: Plan for migrating heilsulykill.is content
- **Size**: 12.6KB

#### `claude-log.md`
- **Type**: Development log
- **Purpose**: Claude AI conversation and development history
- **Size**: 8KB

---

## 🌐 HTML Content Files (GMI Handbook)

### Main Handbook Pages

#### `index.html` (Root)
- **Type**: GMI Handbook homepage
- **Purpose**: Main landing page with overview
- **Contains**:
  - What is Graded Motor Imagery (GMI)
  - Scientific background (neuroplasticity, cortical reorganization)
  - 4-step GMI process overview
  - 12-16 week timeline
  - Indications and contraindications
  - Assessment tools (VAS, DASH, ROM, BPIQ)
  - Referral criteria
  - Research references (Moseley, Ramachandran, NOI Group)
- **Language**: Icelandic
- **Size**: 16.8KB

#### `skref1.html`
- **Type**: GMI Step 1 page
- **Purpose**: Laterality Recognition training
- **Contains**:
  - Cortical reorganization in CRPS
  - 80% accuracy goal (NOI Group standard)
  - Recognise App setup and instructions
  - Image types: Vanilla → Context → Abstract
  - 2-3 week protocol (5 min × 8/day)
  - Progress tracking tables
  - Troubleshooting guide
  - Patient education in Icelandic
- **Language**: Icelandic
- **Size**: 20.4KB

#### `skref2.html`
- **Type**: GMI Step 2 page
- **Purpose**: Explicit Motor Imagery training
- **Contains**:
  - Neurophysiology: Implicit vs Explicit imagery
  - 1st person vs 3rd person perspective
  - 3 full guided imagery scripts with timing
  - 3-week progression protocol
  - VMIQ (Vividness of Motor Imagery Questionnaire)
  - Functional integration with ADL
  - Troubleshooting for common issues
  - Patient education
- **Language**: Icelandic
- **Size**: 19.3KB

#### `skref3.html`
- **Type**: GMI Step 3 page
- **Purpose**: Mirror Therapy
- **Contains**:
  - Mirror neuron system and mechanism
  - Equipment guide with prices (1,000-80,000 ISK)
  - Icelandic and international purchasing links
  - Setup instructions (upper and lower extremity)
  - 3-4 week exercise progression
  - Week-by-week exercises with detailed descriptions
  - Troubleshooting (mirror rejection, headaches)
  - Safety protocols
- **Language**: Icelandic
- **Size**: 21.5KB

#### `skref4.html`
- **Type**: GMI Step 4 page (Innovation)
- **Purpose**: Desensitization protocol
- **Contains**:
  - Central sensitization (allodynia, hyperalgesia)
  - Texture hierarchy: Silk → Sandpaper (6 levels)
  - DIY desensitization kit (3,000-5,000 ISK)
  - Materials list with Icelandic sources
  - 5-6 week progressive protocol
  - Application technique and proper method
  - GMI integration strategies
  - ADL functional application
  - Long-term maintenance
  - Progress tracking logs
- **Language**: Icelandic
- **Size**: 29.5KB
- **Note**: This is Hrefna's innovative addition to traditional 3-step GMI

---

## 📁 public/ Directory

### HTML Files

#### `public/index.html`
- **Type**: Chat app frontend HTML
- **Purpose**: Entry point for Durable Objects chat application
- **Contains**:
  - Skeleton CSS framework
  - React mount point (#root)
  - Basic chat app layout
  - Links to normalize.css and skeleton.css
- **Size**: ~1.5KB
- **Framework**: Skeleton CSS

### CSS Files

#### `public/css/normalize.css`
- **Type**: CSS reset
- **Purpose**: Normalize browser styles for consistency

#### `public/css/skeleton.css`
- **Type**: CSS framework
- **Purpose**: Lightweight responsive grid framework

#### `public/styles.css`
- **Type**: Custom styles
- **Purpose**: Chat app specific styling

### Assets

#### `public/favicon.ico`
- **Type**: Favicon
- **Purpose**: Browser tab icon

---

## 💻 Source Code

### Server Code

#### `src/server/index.ts`
- **Type**: TypeScript server code
- **Purpose**: Cloudflare Durable Objects chat server
- **Contains**:
  - Chat class extending PartyServer
  - WebSocket message handling
  - SQL storage for messages (CREATE TABLE, INSERT, SELECT)
  - Broadcast functionality
  - Connection management
  - Hibernation support
- **Size**: ~2.5KB
- **Dependencies**: partyserver, shared types

#### `src/server/tsconfig.json`
- **Type**: TypeScript config (server)
- **Purpose**: Server-specific TypeScript settings

#### `src/server/worker-configuration.d.ts`
- **Type**: TypeScript declarations
- **Purpose**: Cloudflare Worker type definitions

### Client Code

#### `src/client/index.tsx`
- **Type**: React TypeScript
- **Purpose**: Chat client application
- **Contains**:
  - React app with react-router
  - PartySocket integration
  - Chat message rendering
  - Real-time WebSocket connection
  - Message state management
  - Random name assignment
  - Room-based routing
- **Size**: ~4KB
- **Dependencies**: react, react-dom, react-router, partysocket, nanoid

#### `src/client/tsconfig.json`
- **Type**: TypeScript config (client)
- **Purpose**: Client-specific TypeScript settings

### Shared Code

#### `src/shared.ts`
- **Type**: TypeScript shared types
- **Purpose**: Common types used by both client and server
- **Contains**:
  - ChatMessage type definition
  - Message union type (add/update/all)
  - Names array for random user assignment
- **Size**: ~1.5KB

---

## 📦 Archive Files

### Deployment Packages

#### `gmi-final-deployment.tar.gz`
- **Type**: Compressed archive
- **Purpose**: Complete deployment package
- **Size**: 30.9KB

#### `gmi-handbook-complete.zip`
- **Type**: ZIP archive
- **Purpose**: Full project backup with all files
- **Size**: 36.6KB

#### `gmi-mcp-deployment.tar.gz`
- **Type**: Compressed archive
- **Purpose**: MCP-specific deployment package
- **Size**: 30.8KB

#### `gmi-public-only.zip`
- **Type**: ZIP archive
- **Purpose**: Only public HTML files for Cloudflare Pages
- **Contents**: index.html, skref1-4.html
- **Size**: 29.5KB

#### `gmi-site.tar.gz`
- **Type**: Compressed archive
- **Purpose**: GMI handbook site files
- **Size**: 22KB

---

## 📊 Project Statistics

### Total Files: 34

#### By Type:
- **Configuration**: 4 files (package.json, wrangler.json, tsconfig.json, .gitignore)
- **Documentation**: 9 files (README, DEPLOYMENT, TODO, etc.)
- **HTML Content**: 5 files (GMI handbook pages)
- **Source Code**: 6 files (TypeScript/React)
- **Archive Files**: 5 files (deployment packages)
- **Assets**: 5 files (CSS, favicon)

#### By Category:
- **GMI Handbook Content**: 5 HTML files (~107KB total)
- **Chat Application**: 6 source files + configs
- **Documentation**: 9 markdown files (~50KB total)
- **Build/Deploy**: 5 archive files (~160KB total)

---

## 🎯 Primary Components

### 1. GMI Handbók (Icelandic Medical Handbook)
**Files**: index.html, skref1.html, skref2.html, skref3.html, skref4.html
- Evidence-based CRPS treatment protocols
- 12-16 week GMI program
- Professional content for occupational therapists
- Patient education sections
- Icelandic medical terminology

### 2. Durable Objects Chat Application
**Files**: src/server/index.ts, src/client/index.tsx, src/shared.ts
- Real-time WebSocket chat
- Cloudflare Durable Objects backend
- React frontend with PartyKit
- Message persistence with SQL
- Room-based conversations

### 3. Deployment Infrastructure
**Files**: wrangler.json, package.json, deployment docs
- Cloudflare Workers configuration
- TypeScript build setup
- Multiple deployment options
- Custom domain support (gmi.eyjar.app)

---

## 🔄 Migration Notes

### Files to Keep Active:
- All `src/` directory files (active development)
- `package.json` and `package-lock.json`
- `wrangler.json`
- `tsconfig.json`
- `.gitignore`
- `README.md`

### Files to Move to old/:
- All GMI handbook HTML files (index.html, skref1-4.html)
- All deployment documentation except DEPLOYMENT.md
- All archive files (.tar.gz, .zip)
- PROJECT-SUMMARY.md
- TODO.md
- HEILSULYKILL-MIGRATION-PLAN.md
- claude-log.md
- MCP documentation files

### Files in public/ Directory:
- Keep if needed for chat app
- Review and potentially move to old/ if replacing with GMI content

---

## 📝 Technical Architecture

### Stack Summary:
- **Frontend**: React 18 + TypeScript
- **Backend**: Cloudflare Workers + Durable Objects
- **Real-time**: PartyKit WebSocket library
- **Storage**: Durable Objects SQL
- **CSS Framework**: Pico CSS (GMI) + Skeleton (Chat)
- **Build**: esbuild
- **Deploy**: Cloudflare Pages/Workers
- **Domain**: gmi.eyjar.app

### Data Flow:
1. Client connects via PartySocket
2. WebSocket to Durable Objects Chat class
3. Messages stored in SQL (hibernation support)
4. Broadcast to all connected clients
5. State sync on reconnection

---

## 🎨 Design System

### GMI Handbook:
- **Framework**: Pico CSS v2
- **Font**: Merriweather (Google Fonts)
- **Colors**:
  - Blue (#3498db) - highlights
  - Yellow (#ffc107) - warnings
  - Green (#28a745) - success
  - Purple gradient - step cards
- **Responsive**: Mobile-first design
- **Print-friendly**: Optimized for printing

### Chat Application:
- **Framework**: Skeleton CSS
- **Layout**: Grid-based responsive
- **Minimal**: Clean, functional design

---

## 🔗 External Dependencies

### NPM Packages:
- **react** (^18.0.0) - UI framework
- **react-dom** (^18.0.0) - React DOM rendering
- **react-router** (7.6.3) - Client-side routing
- **partyserver** (0.0.66) - Durable Objects WebSocket server
- **partysocket** (1.1.3) - WebSocket client library
- **nanoid** (5.1.5) - ID generation
- **esbuild** (0.25.2) - JavaScript bundler
- **typescript** (5.8.3) - Type checking
- **wrangler** (4.21.x) - Cloudflare deployment CLI

### CDN Resources:
- Pico CSS v2 (picocss.com)
- Google Fonts (Merriweather)

---

## 📚 Content Sources

### GMI Handbook Research:
- **NOI Group**: Neuro Orthopaedic Institute protocols
- **Moseley, G.L.**: Original GMI research (2004, 2006)
- **Ramachandran, V.S.**: Mirror therapy mechanisms (1996)
- **Bowering, K.J.**: Systematic review (2013)
- **Flor, H.**: Cortical reorganization (2006)
- **Hrefna**: Desensitization innovation

### Chat Template:
- Cloudflare Durable Objects template
- PartyKit documentation

---

## 🚀 Deployment Status

### Current State:
- ✅ GMI HTML pages complete (5 pages, 107KB)
- ✅ Chat application functional (Durable Objects)
- ⏸️ Not yet deployed to production
- ⏸️ Custom domain not yet configured

### Ready for Deployment:
- All HTML content is complete and production-ready
- Chat backend is functional
- Configuration files are set up
- Multiple deployment packages prepared

### Next Steps:
1. Choose deployment method (Pages vs Workers)
2. Deploy to Cloudflare
3. Configure DNS for gmi.eyjar.app
4. Test production environment
5. Migrate heilsulykill.is content (future phase)

---

## 📄 License & Credits

### Content:
- **Proprietary**: GMI Handbók content
- **Owner**: Vertis (vertis.is)
- **Client**: Hrefna Óskarsdóttir
- **Developer**: Omar (omar@omaromar.net)

### Open Source Components:
- React (Meta, MIT License)
- PartyKit (MIT License)
- Pico CSS (MIT License)
- Skeleton CSS (MIT License)

---

**Document Created**: 2025-10-04
**Last Updated**: 2025-10-04
**Purpose**: Complete file inventory before archival migration
**Total Files Documented**: 34
**Total Project Size**: ~500KB

---

## 🔍 Quick File Finder

### Need to find a specific file type?

**Configuration**: `*.json`, `*.toml`, `.gitignore`
**Documentation**: `*.md`
**HTML Content**: `*.html` (root and public/)
**Source Code**: `src/**/*.ts`, `src/**/*.tsx`
**Styles**: `public/css/*.css`
**Archives**: `*.tar.gz`, `*.zip`

### Search by Purpose:

**GMI Medical Content**: index.html, skref1-4.html
**Chat Functionality**: src/server/index.ts, src/client/index.tsx
**Deployment**: wrangler.json, DEPLOYMENT.md, archive files
**Project Planning**: TODO.md, PROJECT-SUMMARY.md
**Type Definitions**: *.d.ts, tsconfig.json, src/shared.ts
