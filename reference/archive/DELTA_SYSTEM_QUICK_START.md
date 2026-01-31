# DELTA EXTRACTION SYSTEM - QUICK START

**Date:** January 11, 2026  
**Status:** Ready for Chapter 1 delta extraction

---

## SYSTEM OVERVIEW

**Old approach:** Full extraction per chapter → competing definitions  
**New approach:** Delta extraction per chapter → one evolving canonical database

**Files created:**
1. DELTA_EXTRACTION_GUIDE.md - How to extract deltas
2. MERGE_PROTOCOL.md - How to review and merge deltas
3. CHAPTER_DELTA_EXTRACTION_PROMPT.md - Prompt for Opus

---

## SETUP COMPLETE ✅

**You've already:**
- ✅ Renamed prologue-entities.json → entity-database-canonical.json
- ✅ Moved it to reference/knowledge-graph/
- ✅ Deleted individual chapter extractions

**Now install new files:**
1. Save the 3 files I provided
2. Place in your VS Code project:
   - `reference/DELTA_EXTRACTION_GUIDE.md`
   - `reference/MERGE_PROTOCOL.md`
   - `reference/CHAPTER_DELTA_EXTRACTION_PROMPT.md`

---

## WORKFLOW: PROCESSING EACH CHAPTER

### Step 1: Delta Extraction (Opus in VS Code)

**In VS Code:**
1. Open Copilot Chat
2. Select **Opus 4.5**
3. Open `CHAPTER_DELTA_EXTRACTION_PROMPT.md`
4. Copy entire prompt (replace [X] with chapter number)
5. Paste into Opus chat
6. Opus will:
   - Read canonical database
   - Read delta extraction guide
   - Process chapter
   - Create `chapter-##-delta.json` in `editorial/extractions/deltas/`
   - Provide summary report

**Time:** 30-60 minutes per chapter

---

### Step 2: Delta Review (You)

**Open the delta JSON file Opus created**

**Review three sections:**

**UPDATES:**
- Does this actually add value?
- Is it accurate?
- Approve / Refine / Reject each one

**ADDITIONS:**
- Is this genuinely new?
- Add / Merge with existing / Trim

**CONTRADICTIONS:**
- Which definition is correct?
- Critical / Moderate / Minor severity?
- Canonical wins / Chapter wins / Synthesize / Flag for rewrite

**Use MERGE_PROTOCOL.md as your guide**

**Time:** 15-30 minutes per chapter

---

### Step 3: Merge into Canonical (You)

**Backup first:**
```bash
cp reference/knowledge-graph/entity-database-canonical.json \
   reference/knowledge-graph/entity-database-canonical-backup-$(date +%Y%m%d).json
```

**Apply approved changes:**
1. Open `entity-database-canonical.json`
2. Apply UPDATES (add examples, refine definitions, etc.)
3. Add ADDITIONS (new entities)
4. Resolve CONTRADICTIONS (update as decided)
5. Add evolution log entries to affected entities

**Save and validate JSON**

**Time:** 15-30 minutes per chapter

---

### Step 4: Log and Commit

**Create/update logs:**
- `reference/knowledge-graph/evolution-log.md` (track growth)
- `reference/knowledge-graph/contradiction-log.md` (track resolutions)
- `reference/knowledge-graph/trimmed-concepts-log.md` (track cuts)

**Commit:**
```bash
git add .
git commit -m "Merge Chapter X deltas: [summary]"
git push
```

**Time:** 5 minutes

---

### Step 5: Repeat for Next Chapter

Total time per chapter: ~1-2 hours (including Opus processing)

---

## FILE LOCATIONS

```
LIFE IN THE SLUG LANE/
├── reference/
│   ├── DELTA_EXTRACTION_GUIDE.md           (NEW - install this)
│   ├── MERGE_PROTOCOL.md                   (NEW - install this)
│   ├── CHAPTER_DELTA_EXTRACTION_PROMPT.md  (NEW - install this)
│   ├── ENTITY_EXTRACTION_GUIDE.md          (existing)
│   └── KNOWLEDGE_SCHEMA.md                 (existing)
│
├── reference/knowledge-graph/
│   ├── entity-database-canonical.json      (YOUR REFINED PROLOGUE - master)
│   ├── evolution-log.md                    (CREATE after first merge)
│   ├── contradiction-log.md                (CREATE after first merge)
│   └── trimmed-concepts-log.md             (CREATE after first merge)
│
└── editorial/extractions/deltas/
    ├── chapter-01-delta.json               (Opus creates these)
    ├── chapter-02-delta.json
    └── ...
```

---

## FIRST CHAPTER: IMMEDIATE NEXT STEPS

### Now (Setup - 5 minutes)

1. **Create log files** (empty for now):
   ```bash
   touch reference/knowledge-graph/evolution-log.md
   touch reference/knowledge-graph/contradiction-log.md
   touch reference/knowledge-graph/trimmed-concepts-log.md
   ```

2. **Install the 3 new files** I provided:
   - DELTA_EXTRACTION_GUIDE.md → `reference/`
   - MERGE_PROTOCOL.md → `reference/`
   - CHAPTER_DELTA_EXTRACTION_PROMPT.md → `reference/`

3. **Create deltas folder**:
   ```bash
   mkdir -p editorial/extractions/deltas
   ```

4. **Commit setup**:
   ```bash
   git add .
   git commit -m "Setup delta extraction system"
   git push
   ```

---

### Next (Chapter 1 Delta - 30-60 minutes)

**In VS Code with Opus 4.5:**
1. Open Copilot Chat
2. Select Opus 4.5
3. Paste Chapter 1 delta extraction prompt:

```
[Use the full prompt from CHAPTER_DELTA_EXTRACTION_PROMPT.md, 
 replacing [X] with 1 and pointing to manuscript/03-chapter-1.md]
```

4. Opus processes and creates `chapter-01-delta.json`
5. Opus provides summary report

---

### After Opus Completes (Review & Merge - 30-60 minutes)

**You review using MERGE_PROTOCOL.md:**
1. Open `editorial/extractions/deltas/chapter-01-delta.json`
2. Review each UPDATE, ADDITION, CONTRADICTION
3. Make decisions (approve/refine/reject, etc.)
4. Merge approved changes into canonical
5. Log changes
6. Commit

---

## BENEFITS YOU'LL SEE

**Immediate:**
- No competing definitions
- Explicit concept evolution
- Contradictions surface early
- Forced clarity and consolidation

**Long-term:**
- Tight, consistent foundations
- Clean knowledge graph
- Easy to track how concepts grew
- Manuscript issues identified early
- One canonical source of truth

---

## TROUBLESHOOTING

**Issue:** Opus extracts mere mentions as updates  
**Fix:** Reject those updates - only real additions count

**Issue:** Opus misses a new entity  
**Fix:** Add it manually following ADDITION schema in delta file

**Issue:** Unsure if something is new or overlooked  
**Fix:** Extract as ADDITION with `integration_recommendation: "flag_for_review"` - you'll decide

**Issue:** Contradiction seems impossible to resolve  
**Fix:** Log in critical-issues-log.md, may need manuscript rewrite

---

## DECISION LOG ENTRY

**Add to DECISION_LOG.md:**

```markdown
### D00X: Delta Extraction System
**Date:** January 11, 2026  
**Decision:** Implement delta extraction system for chapters following Prologue canonical establishment.

**Rationale:**
- Full extraction per chapter creates competing definitions
- Need one evolving canonical database, not multiple standalone extractions
- Delta extraction makes evolution explicit and prevents concept drift
- Forces resolution of contradictions and consolidation of branches

**Implementation:**
- DELTA_EXTRACTION_GUIDE.md (extraction process)
- MERGE_PROTOCOL.md (review and integration process)
- CHAPTER_DELTA_EXTRACTION_PROMPT.md (Opus prompt)
- entity-database-canonical.json (master source of truth)
- Three logs: evolution, contradiction, trimmed concepts

**Impact:**
- Tighter foundations as Joshua requested
- Explicit tracking of concept evolution
- Early identification of manuscript inconsistencies
- Clean knowledge graph for content generation

**Status:** ✅ Implemented, ready for Chapter 1 delta extraction
```

---

## READY TO START?

**You have everything you need:**
- ✅ Canonical database (your refined Prologue)
- ✅ Delta extraction guide
- ✅ Merge protocol
- ✅ Opus prompt template
- ✅ This quick start guide

**Next action:** Install the 3 new files, create log files, commit setup, then run Chapter 1 delta extraction with Opus.

---

**This system will give you exactly the "tightening" you described. Every chapter becomes a quality control point where you refine, consolidate, and strengthen the foundations.**
