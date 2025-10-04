# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**GMI Handbók + Heilsulykill Platform** - A healthcare platform combining a professional Graded Motor Imagery (GMI) handbook for Icelandic occupational therapists treating CRPS patients with real-time chat functionality powered by Cloudflare Durable Objects.

**Target Domain**: gmi.eyjar.app
**Primary Language**: Icelandic (Íslenska) with English technical terms

## Core Architecture

### Implementation Status

This repository is transitioning from legacy HTML to a modern React/Cloudflare Workers platform:

1. **Legacy HTML Pages** (archived in old/ directory) - Complete 5-page GMI handbook
   - `old/index.html` - GMI overview and scientific background
   - `old/skref1-4.html` - Four treatment steps (Laterality, Motor Imagery, Mirror Therapy, Desensitization)
   - Uses Pico CSS framework
   - Self-contained, production-ready content (~107KB total)
   - **Status**: ✅ Complete, archived for reference

2. **React + Cloudflare Workers App** (src/ directory) - Modern real-time platform
   - Frontend: React 18 + TypeScript + React Router 7
   - Backend: Cloudflare Workers + Durable Objects
   - Real-time: PartyKit WebSocket integration
   - **Status**: 🔄 In active development

### Request Flow

```
User Request
    ↓
Cloudflare Worker (src/server/index.ts)
    ↓
├─→ Static Assets (env.ASSETS.fetch) for HTML/CSS
├─→ PartyKit Router (routePartykitRequest) for WebSocket chat
└─→ Chat Durable Object (Chat class) for persistent state
```

### Durable Objects Chat Architecture

The `Chat` class in `src/server/index.ts`:
- **Hibernation enabled** - reduces costs when inactive
- **SQL persistence** - messages stored in Durable Objects SQL
- **Lifecycle hooks**:
  - `onStart()` - creates SQL table, loads message history
  - `onConnect()` - sends full message history to new clients
  - `onMessage()` - broadcasts to all clients, saves to SQL

### Client-Server Communication

Message types (defined in `src/shared.ts`):
- `{type: "add", ...ChatMessage}` - new message
- `{type: "update", ...ChatMessage}` - edit existing message
- `{type: "all", messages: ChatMessage[]}` - full history sync

PartySocket automatically handles WebSocket connection, reconnection, and JSON serialization.

## Development Commands

### Local Development
```bash
npm run dev              # Start Wrangler dev server on localhost:8787
```

This command:
- Runs esbuild to bundle React client → `public/dist/index.js`
- Starts Cloudflare Workers local emulator
- Enables hot reload for both client and server code
- Provides local Durable Objects instance

### Type Checking & Validation
```bash
npm run check            # TypeScript check + dry-run deploy
npm run cf-typegen       # Generate Cloudflare Worker types
```

The `check` script validates:
1. Client TypeScript compilation (`src/client/tsconfig.json`)
2. Server TypeScript compilation (`src/server/tsconfig.json`)
3. Wrangler configuration validity (dry-run deploy)

### Deployment
```bash
npm run deploy           # Deploy to Cloudflare Workers production
wrangler domains add gmi.eyjar.app  # Configure custom domain
```

## Build System

### esbuild Configuration (wrangler.json)
```json
"build": {
  "command": "esbuild src/client/index.tsx --bundle --splitting --format=esm --platform=browser --outdir=public/dist"
}
```

Key flags:
- `--splitting` - code splitting for dynamic imports
- `--format=esm` - ES modules (required for splitting)
- `--bundle` - single build output

### Durable Objects Migration

SQL schema migration in `wrangler.json`:
```json
"migrations": [
  {
    "new_sqlite_classes": ["Chat"],
    "tag": "v1"
  }
]
```

**Important**: When adding new Durable Object classes or changing SQL schema, increment the tag (v2, v3, etc.) to trigger migration.

## TypeScript Project Structure

### Separate tsconfig for Client/Server

- **Client** (`src/client/tsconfig.json`) - Browser environment, DOM types
- **Server** (`src/server/tsconfig.json`) - Cloudflare Workers environment
- **Root** (`tsconfig.json`) - Shared base configuration

Always use the appropriate `--project` flag when running tsc directly.

## Content Guidelines

### Icelandic Medical Terminology

The GMI handbook uses professional Icelandic medical terms with English equivalents in parentheses:
- **Iðjuþjálfar** = Occupational therapists
- **Verkjadeild** = Pain clinic
- **Námskeið** = Courses
- **Úrræði** = Resources/support services

When editing content, maintain this bilingual pattern for technical terms.

### Evidence-Based Content

All GMI protocols reference:
- **NOI Group** (Neuro Orthopaedic Institute) protocols
- **Moseley, G.L.** (2004, 2006) research
- **Ramachandran, V.S.** mirror therapy studies

Do not modify medical protocols without referencing peer-reviewed sources.

## Cloudflare-Specific Patterns

### Asset Handling

The worker serves static files via the `ASSETS` binding:
```typescript
env.ASSETS.fetch(request)
```

This binding points to `./public` directory (configured in wrangler.json). All files in `public/` are uploaded as static assets.

### PartyKit Request Routing

```typescript
routePartykitRequest(request, { ...env })
```

This function:
- Intercepts WebSocket upgrade requests
- Routes to appropriate Durable Object based on `party` and `room` params
- Returns `null` for non-WebSocket requests (falls through to ASSETS)

### SQL in Durable Objects

Use `this.ctx.storage.sql.exec()` for queries:
```typescript
this.ctx.storage.sql.exec(`SELECT * FROM messages`).toArray()
```

**Security Note**: Current implementation uses string interpolation for SQL. Consider parameterized queries for production user input.

## Project Phases

Current implementation status:

1. **Phase 1: GMI HTML** ✅ Complete - 5 standalone HTML pages
2. **Phase 2: Heilsulykill Scraping** 🔄 Planned - see `HEILSULYKILL-MIGRATION-PLAN.md`
3. **Phase 3: React Integration** ⏸️ Pending - convert HTML to React components
4. **Phase 4: Chat Integration** ⏸️ Pending - embed chat in GMI pages
5. **Phase 5: WordPress Local** ⏸️ Pending - Docker dev environment
6. **Phase 6: Production Deploy** ⏸️ Pending - live on gmi.eyjar.app

## File Organization Notes

### Root Directory Clutter

The root directory contains:
- Original GMI HTML files (`index.html`, `skref1-4.html`) - legacy content
- Multiple deployment archives (`.tar.gz`, `.zip`) - one-time deployment packages
- Various documentation files

**Archival Plan**: Most root-level files will move to `old/` directory. See `FILE-OVERVIEW.md` for complete inventory and migration notes.

### Active Development Files

Keep these in active use:
- `src/` - all TypeScript source code
- `package.json`, `package-lock.json` - dependencies
- `wrangler.json` - Cloudflare configuration
- `tsconfig.json` - TypeScript config
- `.gitignore` - git exclusions
- `README.md`, `CLAUDE.md` - documentation

## Testing

Currently no automated tests. When adding tests:
- Use **Vitest** (compatible with Cloudflare Workers)
- Mock Durable Objects storage with `unstable_dev` API
- Test WebSocket connections with PartyKit test utilities

## Deployment Target

**Production Domain**: gmi.eyjar.app
**Cloudflare Account**: Vertis.is account
**Environment Variables**: None required (all configuration in wrangler.json)

## Additional Context

- **Client**: Reykjavik City Healthcare / Hrefna Óskarsdóttir
- **Innovation**: Skref 4 (Desensitization) is unique addition to traditional 3-step GMI
- **Proprietary Content**: Medical protocols are proprietary to Vertis.is
- **Development Log**: See `claude-log.md` for AI-assisted development history
