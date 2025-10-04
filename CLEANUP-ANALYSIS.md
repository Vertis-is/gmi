# 🧹 GMI Project Cleanup Analysis

**Generated**: 2025-10-04
**Purpose**: Identify duplicates, outdated files, and create cleanup plan

---

## 📊 Current State

**Total Files**: 30+ files across root, public/, src/, and gmi-vefsidur/
**Issue**: Multiple duplicates, outdated deployment docs, unnecessary archives

---

## 🔴 DUPLICATES FOUND

### 1. GMI HTML Content (DUPLICATE)

**Location A - Root Directory** (✅ KEEP - Most Complete):
- `index.html` (341 lines, Merriweather font, complete content)
- `skref1.html` (Laterality Recognition)
- `skref2.html` (Motor Imagery)
- `skref3.html` (Mirror Therapy)
- `skref4.html` (Desensitization) ✅ **Only this location has Step 4**

**Location B - gmi-vefsidur/** (❌ DELETE - Incomplete, Different Font):
- `gmi-index.html` (419 lines, Times New Roman font)
- `gmi-skref1.html`
- `gmi-skref2.html`
- `gmi-skref3.html`
- **Missing skref4** ❌

**Action**: 
- ✅ Keep root HTML files (index.html, skref1-4.html)
- ❌ DELETE entire `gmi-vefsidur/` directory

---

### 2. Deployment Documentation (MULTIPLE DUPLICATES)

**Primary Guide** (✅ KEEP):
- `DEPLOYMENT.md` - Comprehensive Icelandic deployment guide (6KB)

**Duplicate/Outdated Guides** (❌ DELETE):
- `MCP-DEPLOYMENT-GUIDE.md` (4KB) - Redundant with DEPLOYMENT.md
- `MCP-FINAL-DEPLOYMENT.md` (6.1KB) - Redundant with DEPLOYMENT.md
- `ONE-COMMAND-DEPLOY.md` (2.2KB) - Subset of DEPLOYMENT.md
- `QUICK-START.md` (2.5KB) - Subset of DEPLOYMENT.md
- `PROJECT-SUMMARY.md` (9KB) - Project history, not needed going forward

**Action**: 
- ✅ Keep `DEPLOYMENT.md` only
- ❌ DELETE all other deployment guides

---

### 3. Archive Files (NO LONGER NEEDED)

All deployment packages are outdated and can be regenerated:

❌ DELETE:
- `gmi-final-deployment.tar.gz` (30.9KB)
- `gmi-handbook-complete.zip` (36.6KB)
- `gmi-mcp-deployment.tar.gz` (30.8KB)
- `gmi-public-only.zip` (29.5KB)
- `gmi-site.tar.gz` (22KB)

**Total Space to Reclaim**: ~160KB

**Rationale**: 
- One-time deployment packages
- Can be regenerated with `npm run deploy`
- Git history preserves old versions

---

## ✅ ACTIVE FILES TO KEEP

### Configuration (Keep in Root)
- `package.json` ✅
- `package-lock.json` ✅
- `wrangler.json` ✅
- `tsconfig.json` ✅
- `.gitignore` ✅

### Source Code (Keep All)
- `src/client/` ✅
- `src/server/` ✅
- `src/shared.ts` ✅

### Public Assets (Keep All)
- `public/index.html` (Chat app) ✅
- `public/css/` ✅
- `public/styles.css` ✅
- `public/favicon.ico` ✅

### Essential Documentation (Keep in Root)
- `README.md` ✅ - Main project documentation
- `CLAUDE.md` ✅ - AI coding guidance
- `DEPLOYMENT.md` ✅ - Deployment instructions

---

## 📦 FILES TO ARCHIVE (Move to old/)

These are historical/planning documents:

**Move to `old/` directory**:
- `index.html, skref1-4.html` (Legacy GMI HTML - before React migration)
- `TODO.md` (Project planning - historical)
- `HEILSULYKILL-MIGRATION-PLAN.md` (Future migration plan)
- `claude-log.md` (Development log)
- `FILE-OVERVIEW.md` (Inventory - now outdated)
- `PROJECT-SUMMARY.md` (Project history)
- `MCP-DEPLOYMENT-GUIDE.md`
- `MCP-FINAL-DEPLOYMENT.md`
- `ONE-COMMAND-DEPLOY.md`
- `QUICK-START.md`

**Rationale**: 
- Not needed for active development
- Historical reference only
- Keeps root clean

---

## 🗑️ FILES TO DELETE COMPLETELY

### Delete Immediately:
- ❌ `gmi-vefsidur/` directory (entire folder - duplicates)
- ❌ All `.tar.gz` and `.zip` files (5 archive files)

### Rationale:
- Duplicates with worse content
- Archives can be regenerated
- No historical value

---

## 📋 CLEANUP PLAN

### Phase 1: Delete Duplicates & Archives (SAFE)

```bash
# Navigate to project
cd C:\git\gmi

# Delete duplicate HTML directory
rmdir /s gmi-vefsidur

# Delete all archive files
del *.tar.gz
del *.zip
```

**Impact**: ✅ Safe - Removes 160KB+ of unnecessary files

---

### Phase 2: Archive Historical Files

```bash
# Create old directory
mkdir old

# Move legacy HTML to old/
move index.html old\
move skref1.html old\
move skref2.html old\
move skref3.html old\
move skref4.html old\

# Move historical docs to old/
move TODO.md old\
move HEILSULYKILL-MIGRATION-PLAN.md old\
move claude-log.md old\
move FILE-OVERVIEW.md old\
move PROJECT-SUMMARY.md old\
move MCP-DEPLOYMENT-GUIDE.md old\
move MCP-FINAL-DEPLOYMENT.md old\
move ONE-COMMAND-DEPLOY.md old\
move QUICK-START.md old\
```

**Impact**: ⚠️ Moderate - Preserves history but cleans root

---

### Phase 3: Update Documentation

After cleanup, update these files:

**README.md**:
- Remove references to legacy HTML files
- Focus on React/Cloudflare architecture
- Update file structure section

**CLAUDE.md**:
- Update file locations section
- Remove references to old/ files
- Add note about archived content

---

## 📊 Before & After Comparison

### BEFORE (Current State):
```
C:\git\gmi\
├── 5 GMI HTML files (root)
├── 4 duplicate HTML files (gmi-vefsidur/)
├── 5 deployment guides
├── 5 archive files
├── 9 documentation files
├── src/ (active code)
├── public/ (active assets)
└── configs (4 files)

Total: ~30 files in root
```

### AFTER (Cleaned):
```
C:\git\gmi\
├── src/ (active code) ✅
├── public/ (active assets) ✅
├── old/ (archived legacy content) 📦
├── package.json, package-lock.json ✅
├── wrangler.json, tsconfig.json ✅
├── .gitignore ✅
├── README.md ✅
├── CLAUDE.md ✅
└── DEPLOYMENT.md ✅

Total: ~10 files in root (organized)
```

---

## ⚠️ Safety Notes

### Before Cleanup:
1. ✅ **Commit current state to git**:
   ```bash
   git add .
   git commit -m "Snapshot before cleanup"
   ```

2. ✅ **Verify git remote is up to date**:
   ```bash
   git push
   ```

3. ✅ **Create backup** (optional):
   ```bash
   # Full backup
   7z a gmi-backup-before-cleanup.7z C:\git\gmi\
   ```

### During Cleanup:
- Do NOT delete `src/` or `public/` directories
- Do NOT delete `package.json` or `wrangler.json`
- Do NOT delete `.git/` directory

### After Cleanup:
1. ✅ **Test build**:
   ```bash
   npm run check
   ```

2. ✅ **Test local dev**:
   ```bash
   npm run dev
   ```

3. ✅ **Commit cleanup**:
   ```bash
   git add .
   git commit -m "Cleanup: Remove duplicates, archive legacy files"
   git push
   ```

---

## 🎯 Recommendation

**Execute Phase 1 IMMEDIATELY**:
- Deletes duplicates and archives (160KB)
- Zero risk to active code
- Cleans up clutter

**Execute Phase 2 SOON**:
- Moves legacy HTML to old/
- Preserves history
- Cleans root directory

**Execute Phase 3 LATER**:
- Update documentation
- After React components are ready

---

## 📊 Expected Results

### Space Saved:
- Archives deleted: ~160KB
- Duplicates removed: ~100KB
- **Total: ~260KB freed**

### Organization Improvement:
- Root files: 30 → 10 (67% reduction)
- Clear separation: active code vs. archived content
- Easier navigation for AI and developers

### Risk Level:
- **Phase 1**: 🟢 Zero risk (duplicates & archives)
- **Phase 2**: 🟡 Low risk (legacy content moved, not deleted)
- **Phase 3**: 🟢 Zero risk (documentation update)

---

## 🤔 Questions?

**Q: What if I need the old HTML files?**
A: They'll be in `old/` directory and in git history

**Q: Can I regenerate the archive files?**
A: Yes, just run `npm run deploy` or create new archives

**Q: Will this break anything?**
A: No - active code in `src/` and `public/` is untouched

**Q: Should I delete old/ after cleanup?**
A: No - keep it for reference, it's not taking much space

---

**Ready to clean up? Let me know and I'll execute the cleanup plan!** 🧹
