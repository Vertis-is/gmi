# GMI Project TODO List

**Project**: GMI Handbók + Heilsulykill.is Migration + Cloudflare Deployment  
**Target**: gmi.eyjar.app  
**Started**: 2025-10-04  
**Last Updated**: 2025-10-04

---

## 🎯 Project Goals

- [ ] Create professional GMI (Graded Motor Imagery) handbook in Icelandic
- [ ] Migrate heilsulykill.is content to Cloudflare
- [ ] Integrate Cloudflare Durable Objects chat functionality
- [ ] Deploy to gmi.eyjar.app with custom domain
- [ ] Setup WordPress local environment for content management

---

## 📊 Project Status

| Phase | Status | Progress |
|-------|--------|----------|
| Phase 1: GMI HTML Pages | ✅ Complete | 100% |
| Phase 2: Heilsulykill Scraping | 🔄 In Progress | 0% |
| Phase 3: React Integration | ⏸️ Pending | 0% |
| Phase 4: Chat Integration | ⏸️ Pending | 0% |
| Phase 5: WordPress Setup | ⏸️ Pending | 0% |
| Phase 6: Deployment | ⏸️ Pending | 0% |

---

## 🚀 Phase 1: GMI HTML Pages (COMPLETE)

### Completed ✅
- [x] Create index.html (GMI Overview)
- [x] Create skref1.html (Laterality Recognition)
- [x] Create skref2.html (Explicit Motor Imagery)
- [x] Create skref3.html (Mirror Therapy)
- [x] Create skref4.html (Desensitization)
- [x] Add Pico CSS framework
- [x] Create navigation menu
- [x] Add professional styling
- [x] Icelandic translations
- [x] Evidence-based content

### Files Created
- `C:\git\gmi\index.html`
- `C:\git\gmi\skref1.html`
- `C:\git\gmi\skref2.html`
- `C:\git\gmi\skref3.html`
- `C:\git\gmi\skref4.html`

---

## 🔍 Phase 2: Heilsulykill.is Scraping

### High Priority 🔴
- [ ] Get Apify API token
- [ ] Run Website Content Crawler on heilsulykill.is
- [ ] Download scraped data (JSON + files)
- [ ] Verify data completeness
- [ ] Organize content by categories
- [ ] Extract course information
- [ ] Download media files (images, PDFs)

### Medium Priority 🟡
- [ ] Create content mapping spreadsheet
- [ ] Identify unique content types
- [ ] Plan URL structure for migration
- [ ] Document WordPress taxonomy

### Subtasks
```javascript
// Apify Configuration Needed
{
  "startUrls": ["https://heilsulykill.is/"],
  "saveMarkdown": true,
  "saveFiles": true,
  "useSitemaps": true
}
```

---

## ⚛️ Phase 3: React Integration

### High Priority 🔴
- [ ] Convert GMI HTML to React components
- [ ] Setup React Router
- [ ] Create component structure
- [ ] Implement navigation
- [ ] Add state management (if needed)
- [ ] Style with Pico CSS in React

### Components to Create
- [ ] `src/client/components/GMI/Forsida.tsx`
- [ ] `src/client/components/GMI/Skref1.tsx`
- [ ] `src/client/components/GMI/Skref2.tsx`
- [ ] `src/client/components/GMI/Skref3.tsx`
- [ ] `src/client/components/GMI/Skref4.tsx`
- [ ] `src/client/components/Layout/Navigation.tsx`
- [ ] `src/client/components/Layout/Footer.tsx`

### Routes to Define
```tsx
/ → GMI Forsíða
/gmi/skref1 → Laterality Recognition
/gmi/skref2 → Motor Imagery
/gmi/skref3 → Mirror Therapy
/gmi/skref4 → Desensitization
/namskeið → Heilsulykill courses
/chat/:room → Chat rooms
```

---

## 💬 Phase 4: Chat Integration

### High Priority 🔴
- [ ] Review existing Durable Objects chat code
- [ ] Create ChatWidget component
- [ ] Add floating chat button to GMI pages
- [ ] Implement chat overlay/modal
- [ ] Test PartySocket connection
- [ ] Add chat rooms per GMI step

### Features to Implement
- [ ] Real-time messaging
- [ ] User presence indicators
- [ ] Message history
- [ ] Room-based conversations
- [ ] Professional/therapist mode
- [ ] Patient mode

### Chat Integration Points
- [ ] GMI Skref 1 → Chat room: "gmi-skref1"
- [ ] GMI Skref 2 → Chat room: "gmi-skref2"
- [ ] GMI Skref 3 → Chat room: "gmi-skref3"
- [ ] GMI Skref 4 → Chat room: "gmi-skref4"
- [ ] General questions → Chat room: "gmi-general"

---

## 🖥️ Phase 5: WordPress Local Setup

### High Priority 🔴
- [ ] Install Docker Desktop
- [ ] Create docker-compose.yml
- [ ] Start WordPress container
- [ ] Configure WordPress admin
- [ ] Install necessary plugins
- [ ] Setup theme

### Medium Priority 🟡
- [ ] Create import script (import-to-wordpress.js)
- [ ] Map heilsulykill content to WordPress
- [ ] Import courses as custom post type
- [ ] Import events/viðburðir
- [ ] Import organizations/samtök
- [ ] Setup WordPress REST API auth

### Docker Setup
```yaml
# docker-compose.yml needed
- WordPress: Port 8080
- MySQL: Port 3306
- phpMyAdmin: Port 8081
```

### WordPress Plugins Needed
- [ ] Advanced Custom Fields
- [ ] Custom Post Type UI
- [ ] WP REST API extensions
- [ ] Import/Export tools

---

## 🚀 Phase 6: Cloudflare Deployment

### High Priority 🔴
- [ ] Review wrangler.json configuration
- [ ] Update build commands
- [ ] Test local build
- [ ] Deploy to Cloudflare Workers
- [ ] Configure Durable Objects
- [ ] Setup custom domain (gmi.eyjar.app)
- [ ] Configure DNS at Cloudflare
- [ ] Verify SSL certificate

### Build & Deploy
```bash
# Commands needed
npm install
npm run build
wrangler deploy
wrangler domains add gmi.eyjar.app
```

### DNS Configuration
```
Type: CNAME
Name: gmi
Target: [worker-url].workers.dev
Proxy: ✅ Proxied
```

### Cloudflare Services to Configure
- [ ] Workers (main app)
- [ ] Durable Objects (chat)
- [ ] R2 (file storage for heilsulykill assets)
- [ ] Pages (alternative deployment method)
- [ ] Analytics
- [ ] Cache rules

---

## 📝 Content Tasks

### GMI Content
- [ ] Review medical accuracy
- [ ] Add image placeholders
- [ ] Create exercise diagrams
- [ ] Add video links (if available)
- [ ] Proofread Icelandic text
- [ ] Add citations/references

### Heilsulykill Content
- [ ] Map course structure
- [ ] Preserve course metadata
- [ ] Maintain instructor information
- [ ] Keep pricing information
- [ ] Preserve registration links
- [ ] Archive downloadable materials

---

## 🔧 Technical Debt

### Code Quality
- [ ] Add TypeScript strict mode
- [ ] Write unit tests
- [ ] Add E2E tests (Playwright)
- [ ] Setup ESLint
- [ ] Add Prettier
- [ ] Document components
- [ ] Create Storybook (optional)

### Performance
- [ ] Optimize bundle size
- [ ] Add lazy loading
- [ ] Implement code splitting
- [ ] Add service worker
- [ ] Optimize images
- [ ] Setup CDN for assets

### Security
- [ ] Add rate limiting to chat
- [ ] Implement CORS properly
- [ ] Add input sanitization
- [ ] Setup CSP headers
- [ ] Add authentication (if needed)
- [ ] Secure API endpoints

---

## 📚 Documentation

### User Documentation
- [ ] Create user guide for GMI handbook
- [ ] Write therapist instructions
- [ ] Document chat features
- [ ] Create troubleshooting guide
- [ ] Add FAQ section

### Developer Documentation
- [ ] Document architecture
- [ ] API documentation
- [ ] Deployment guide
- [ ] Contributing guidelines
- [ ] Code style guide

### Files to Create
- [ ] `README.md` (comprehensive)
- [ ] `CONTRIBUTING.md`
- [ ] `ARCHITECTURE.md`
- [ ] `API.md`
- [ ] `DEPLOYMENT.md` (update existing)

---

## 🎨 Design Tasks

### UI/UX
- [ ] Create design system
- [ ] Define color palette
- [ ] Choose typography
- [ ] Create icon set
- [ ] Design mobile layouts
- [ ] Add animations
- [ ] Create loading states
- [ ] Design error states

### Accessibility
- [ ] WCAG 2.1 AA compliance
- [ ] Screen reader testing
- [ ] Keyboard navigation
- [ ] Color contrast check
- [ ] Alt text for images
- [ ] ARIA labels

---

## 🐛 Known Issues

### Current Bugs
- None yet - project just started!

### To Investigate
- [ ] Chat connection stability
- [ ] Mobile browser compatibility
- [ ] WordPress import edge cases
- [ ] Cloudflare cold start times

---

## 💡 Future Enhancements

### Nice to Have
- [ ] Multi-language support (EN, IS)
- [ ] Progress tracking for therapists
- [ ] Patient dashboard
- [ ] Exercise video uploads
- [ ] PDF generation of GMI protocols
- [ ] Email notifications
- [ ] Calendar integration
- [ ] Appointment booking

### Advanced Features
- [ ] AI chatbot for Q&A
- [ ] Exercise compliance tracking
- [ ] Data visualization
- [ ] Export patient progress
- [ ] Integration with EMR systems

---

## 📅 Timeline

### Week 1 (Current)
- [x] GMI HTML pages
- [ ] Heilsulykill scraping
- [ ] Project planning

### Week 2
- [ ] React component conversion
- [ ] Chat integration
- [ ] WordPress setup

### Week 3
- [ ] Content import
- [ ] Testing
- [ ] Deployment preparation

### Week 4
- [ ] Production deployment
- [ ] DNS setup
- [ ] Go live!

---

## 🤝 Stakeholders

### Team
- **Developer**: Omar (omaromar.net)
- **Company**: Vertis.is
- **Client**: Reykjavik City (potential)

### Contacts
- Omar: omar@omaromar.net
- Vertis: contact@vertis.is

---

## 📌 Quick Links

- [Cloudflare Dashboard](https://dash.cloudflare.com)
- [Apify Console](https://console.apify.com)
- [GitHub Repo](https://github.com/Vertis-is/gmi)
- [Heilsulykill.is](https://heilsulykill.is)
- [Migration Plan](./HEILSULYKILL-MIGRATION-PLAN.md)
- [Deployment Guide](./DEPLOYMENT.md)

---

## 📝 Notes

### Important Decisions
- Using Cloudflare Workers + Durable Objects (not Pages alone)
- React for frontend (already in template)
- WordPress local for content management
- Apify for web scraping
- Pico CSS for styling

### Questions to Resolve
- [ ] Authentication needed for chat?
- [ ] Analytics platform choice?
- [ ] Backup strategy?
- [ ] Content update workflow?

---

**Last Updated**: 2025-10-04 15:00 UTC  
**Next Review**: Daily updates as we progress
