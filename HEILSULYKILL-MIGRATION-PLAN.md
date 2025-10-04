# 🚀 Heilsulykill.is → Cloudflare Migration Plan

## Verkefnisyfirlit

**Markmið**: Migrate heilsulykill.is í Cloudflare, bæta við GMI handbók með chat functionality

### Þrjú Meginverkefni:

1. **Scrape heilsulykill.is** (Apify Website Content Crawler)
2. **WordPress Local Setup** (Development environment)
3. **GMI + Chat Integration** (Full Cloudflare solution)

---

## 📊 FASI 1: Scrape Heilsulykill.is

### 1.1 Apify Website Content Crawler Setup

```javascript
// Input Configuration fyrir apify/website-content-crawler
{
  "startUrls": [
    {
      "url": "https://heilsulykill.is/"
    }
  ],
  "crawlerType": "playwright:firefox",  // For WordPress sites
  "maxCrawlPages": 9999,                 // Scrape everything
  "maxCrawlDepth": 20,                   // Deep crawl
  "saveMarkdown": true,                   // ✅ For easy migration
  "saveHtml": false,
  "saveHtmlAsFile": true,                // ✅ For debugging
  "saveFiles": true,                      // ✅ Download PDFs, etc.
  "removeElementsCssSelector": "nav, footer, .cookie-banner, .popup",
  "htmlTransformer": "readableText",
  "proxyConfiguration": {
    "useApifyProxy": true
  },
  "useSitemaps": true,                   // ✅ Find all pages
  "respectRobotsTxtFile": true,
  "initialConcurrency": 3,
  "maxConcurrency": 10
}
```

### 1.2 Run Scraper

**Option A - Via Apify Console:**
```bash
1. Go to: https://apify.com/apify/website-content-crawler
2. Paste config from above
3. Click "Start"
4. Wait for completion (5-30 minutes depending on size)
5. Download results as JSON + Files
```

**Option B - Via API (Recommended):**


```javascript
// Run scraper via Apify API
const { ApifyClient } = require('apify-client');

const client = new ApifyClient({
    token: 'YOUR_APIFY_TOKEN', // Get from https://console.apify.com/account/integrations
});

const input = {
    startUrls: [{ url: 'https://heilsulykill.is/' }],
    crawlerType: 'playwright:firefox',
    maxCrawlPages: 9999,
    saveMarkdown: true,
    saveHtmlAsFile: true,
    saveFiles: true,
    useSitemaps: true,
};

// Start the Actor and wait for it to finish
const run = await client.actor('apify/website-content-crawler').call(input);

// Fetch results from the run's dataset
const { items } = await client.dataset(run.defaultDatasetId).listItems();

console.log(`Scraped ${items.length} pages from Heilsulykill.is`);

// Save to local file
const fs = require('fs');
fs.writeFileSync('heilsulykill-data.json', JSON.stringify(items, null, 2));
```

### 1.3 Data Structure

Hver síða í scraped data:

```json
{
  "url": "https://heilsulykill.is/namskeið/streita",
  "crawl": {
    "loadedUrl": "https://heilsulykill.is/namskeið/streita",
    "loadedTime": "2025-10-04T14:00:00.000Z",
    "depth": 1
  },
  "metadata": {
    "canonicalUrl": "https://heilsulykill.is/namskeið/streita",
    "title": "Streita námskeið - Heilsulykill",
    "description": "Námskeið um að takast á við streitu",
    "languageCode": "is"
  },
  "text": "Full text content...",
  "markdown": "# Title\n\nMarkdown content..."
}
```

---

## 🖥️ FASI 2: WordPress Local Setup

### 2.1 Prerequisites

```bash
# Install required software
choco install docker-desktop
choco install nodejs
choco install php
choco install composer
```

### 2.2 Docker WordPress Setup

```bash
# Create project directory
cd C:\git
mkdir heilsulykill-local
cd heilsulykill-local

# Create docker-compose.yml
```

```yaml
# docker-compose.yml
version: '3.8'

services:
  wordpress:
    image: wordpress:latest
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress_data:/var/www/html
    depends_on:
      - db

  db:
    image: mysql:8.0
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
      MYSQL_ROOT_PASSWORD: root_password
    volumes:
      - db_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin:latest
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: root_password

volumes:
  wordpress_data:
  db_data:
```

```bash
# Start WordPress
docker-compose up -d

# Access WordPress at: http://localhost:8080
# Access phpMyAdmin at: http://localhost:8081
```

### 2.3 Import Scraped Data to WordPress

```javascript
// import-to-wordpress.js
const axios = require('axios');
const fs = require('fs');

const WP_URL = 'http://localhost:8080';
const WP_USER = 'admin';
const WP_PASSWORD = 'your-password';

// Get auth token
const auth = Buffer.from(`${WP_USER}:${WP_PASSWORD}`).toString('base64');

// Read scraped data
const scrapedData = JSON.parse(fs.readFileSync('heilsulykill-data.json', 'utf8'));

// Import each page
for (const page of scrapedData) {
  const post = {
    title: page.metadata.title,
    content: page.markdown || page.text,
    status: 'publish',
    excerpt: page.metadata.description,
    meta: {
      original_url: page.url,
      scraped_date: page.crawl.loadedTime
    }
  };

  try {
    const response = await axios.post(
      `${WP_URL}/wp-json/wp/v2/posts`,
      post,
      {
        headers: {
          'Authorization': `Basic ${auth}`,
          'Content-Type': 'application/json'
        }
      }
    );
    console.log(`✅ Imported: ${page.metadata.title}`);
  } catch (error) {
    console.error(`❌ Failed: ${page.metadata.title}`, error.message);
  }
}
```

---

## 🔗 FASI 3: GMI + Chat Integration í Cloudflare

### 3.1 Architecture Overview

```
┌─────────────────────────────────────┐
│     GMI @ gmi.eyjar.app            │
│                                     │
│  ┌──────────────────────────────┐  │
│  │  Forsíða - GMI Overview      │  │
│  │  /                           │  │
│  └──────────────────────────────┘  │
│                                     │
│  ┌──────────────────────────────┐  │
│  │  GMI Handbók                 │  │
│  │  /gmi/skref1                 │  │
│  │  /gmi/skref2                 │  │
│  │  /gmi/skref3                 │  │
│  │  /gmi/skref4                 │  │
│  │                              │  │
│  │  💬 Chat Integration         │  │
│  │  (Durable Objects)           │  │
│  └──────────────────────────────┘  │
│                                     │
│  ┌──────────────────────────────┐  │
│  │  Heilsulykill Content        │  │
│  │  /úrræði/*                   │  │
│  │  /námskeið/*                 │  │
│  │  /viðburðir/*                │  │
│  └──────────────────────────────┘  │
└─────────────────────────────────────┘
```

### 3.2 Project Structure

```
C:\git\gmi\
├── src/
│   ├── client/
│   │   ├── index.tsx          # React app entry
│   │   ├── components/
│   │   │   ├── GMI/
│   │   │   │   ├── Forsida.tsx
│   │   │   │   ├── Skref1.tsx
│   │   │   │   ├── Skref2.tsx
│   │   │   │   ├── Skref3.tsx
│   │   │   │   └── Skref4.tsx
│   │   │   ├── Chat/
│   │   │   │   ├── ChatWindow.tsx
│   │   │   │   └── ChatMessage.tsx
│   │   │   └── Heilsulykill/
│   │   │       ├── CourseList.tsx
│   │   │       └── CourseDetail.tsx
│   │   └── routes.tsx
│   ├── server/
│   │   ├── index.ts           # Worker entry
│   │   └── chat.ts            # Durable Object
│   └── shared.ts
├── public/
│   ├── index.html
│   ├── assets/
│   └── heilsulykill/          # Migrated content
│       └── courses/
└── wrangler.json
```

### 3.3 React Routes Setup

```tsx
// src/client/routes.tsx
import { createBrowserRouter } from 'react-router';
import GMIForsida from './components/GMI/Forsida';
import GMISkref1 from './components/GMI/Skref1';
import GMISkref2 from './components/GMI/Skref2';
import GMISkref3 from './components/GMI/Skref3';
import GMISkref4 from './components/GMI/Skref4';
import HeilsulykillCourses from './components/Heilsulykill/CourseList';
import ChatApp from './components/Chat/ChatWindow';

export const router = createBrowserRouter([
  {
    path: '/',
    element: <GMIForsida />,
  },
  {
    path: '/gmi/skref1',
    element: <GMISkref1 />,
  },
  {
    path: '/gmi/skref2',
    element: <GMISkref2 />,
  },
  {
    path: '/gmi/skref3',
    element: <GMISkref3 />,
  },
  {
    path: '/gmi/skref4',
    element: <GMISkref4 />,
  },
  {
    path: '/namskeið',
    element: <HeilsulykillCourses />,
  },
  {
    path: '/chat/:room?',
    element: <ChatApp />,
  },
]);
```

### 3.4 Chat Integration í GMI síður

```tsx
// src/client/components/GMI/Skref1.tsx
import React, { useState } from 'react';
import { usePartySocket } from 'partysocket/react';
import ChatWidget from '../Chat/ChatWidget';

export default function GMISkref1() {
  const [showChat, setShowChat] = useState(false);

  return (
    <div className="gmi-container">
      <nav className="gmi-nav">
        {/* Navigation */}
      </nav>

      <main className="gmi-content">
        <h1>Skref 1: Laterality Recognition</h1>
        
        {/* GMI content */}
        
        {/* Chat Widget Floating Button */}
        <button 
          className="chat-fab"
          onClick={() => setShowChat(!showChat)}
        >
          💬 Spjalla
        </button>

        {/* Chat Overlay */}
        {showChat && (
          <div className="chat-overlay">
            <ChatWidget room="gmi-skref1" />
          </div>
        )}
      </main>
    </div>
  );
}
```

---

## 🚀 FASI 4: Deployment

### 4.1 Build Configuration

```json
// wrangler.json update
{
  "name": "gmi",
  "compatibility_date": "2025-04-01",
  "main": "src/server/index.ts",
  "assets": {
    "directory": "./public",
    "binding": "ASSETS"
  },
  "routes": [
    { "pattern": "gmi.eyjar.app/*", "zone_name": "eyjar.app" }
  ],
  "durable_objects": {
    "bindings": [
      {
        "name": "Chat",
        "class_name": "Chat"
      }
    ]
  }
}
```

### 4.2 Deploy Commands

```bash
# Install dependencies
npm install

# Build
npm run build

# Deploy to Cloudflare
wrangler deploy

# Custom domain setup
wrangler domains add gmi.eyjar.app
```

### 4.3 DNS Setup

```bash
# At Cloudflare DNS (eyjar.app zone):
Type: CNAME
Name: gmi
Target: gmi.pages.dev (or worker URL)
Proxy: ✅ Proxied (orange cloud)
```

---

## 📋 Checklist

### Phase 1: Scraping ✅
- [ ] Run Website Content Crawler on heilsulykill.is
- [ ] Download JSON + files
- [ ] Verify all pages scraped
- [ ] Organize content by categories

### Phase 2: WordPress Local ✅
- [ ] Docker setup
- [ ] WordPress installation
- [ ] Import scraped content
- [ ] Test locally at localhost:8080

### Phase 3: Integration ✅
- [ ] Create React components for GMI
- [ ] Integrate chat functionality
- [ ] Add Heilsulykill content
- [ ] Test routing

### Phase 4: Deployment ✅
- [ ] Build production bundle
- [ ] Deploy to Cloudflare Workers
- [ ] Configure DNS
- [ ] Test gmi.eyjar.app
- [ ] SSL certificate active

---

## 💰 Cost Estimate

### Apify Scraping
- **Website Content Crawler**: ~$0.50 - $5.00
  - Heilsulykill.is has ~50-200 pages
  - Estimated cost: **$1-2**

### Cloudflare
- **Workers**: $5/month (Paid plan for Durable Objects)
- **Pages**: Free (with 500 builds/month)
- **R2 Storage** (for files): $0.015/GB/month
- **Total Monthly**: **~$5-10**

### WordPress Local
- **Free** (Docker on local machine)

---

## 🔧 Næstu Skref

Viltu að ég:

1. **Keyri scraping núna?** 
   - Run Apify Website Content Crawler
   - Download results

2. **Búi til React components?**
   - Convert GMI HTML → React
   - Add chat integration

3. **Setji upp WordPress?**
   - Docker-compose configuration
   - Import script

Segðu mér hvaða fasi þú vilt byrja á! 🚀
