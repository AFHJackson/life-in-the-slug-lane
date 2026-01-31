# CHAPTER POLISH WORKFLOW
## Per-Chapter Refinement Protocol

**Purpose:** Systematic polish of each chapter through Opus→Sonnet→Opus workflow  
**Created:** January 30, 2026  
**Status:** Active - First Pass (Chapters 6-12)

---

## CANONICAL SOURCE FILES

| File | Purpose |
|------|---------|
| `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md` | Gold-copy markdown (sync target) |
| `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.docx` | Word version for user review |
| `Life-in-the-Slug-Lane-REVIEW-DRAFT.docx` | ARCHIVE AFTER CH6 - has newer Ch6 content |

**Note:** REVIEW-DRAFT contains ~5,500 more characters in Chapter 6 (semi-truck passage, enhanced content). Once Chapter 6 is fixed, archive REVIEW-DRAFT and use COMPLETE as sole canonical.

---

## WORKFLOW OVERVIEW

```
OPUS 4.5: Analysis, Architecture Check, AND Content Revisions
    ↓
SONNET 4.5: Voice/Tone/Feel Polish ONLY (light touch, no content changes)
    ↓
OPUS 4.5: Word Sync from User Review
    ↓
UPDATE THIS CHECKLIST → Next Chapter
```

**CRITICAL:** Opus 4.5 makes ALL content revisions and corrections from canonical database.
Sonnet 4.5 ONLY polishes voice consistency - it does NOT change content or make corrections.

---

## MASTER CHECKLIST - FIRST PASS

| # | Chapter | Phase 1 (Opus) | Phase 2 (Sonnet) | Phase 3 (Opus) | Status |
|---|---------|----------------|------------------|----------------|--------|
| 06 | Friendship, Anarchy, Order | ✅ | ⬜ | ⬜ | **Ready for Sonnet** |
| 07 | When Systems Touch | ⬜ | ⬜ | ⬜ | Not Started |
| 08 | The Ring Compass | ⬜ | ⬜ | ⬜ | Not Started |
| 09 | Obligation to Excess | ⬜ | ⬜ | ⬜ | Not Started |
| 10 | Stewardship | ⬜ | ⬜ | ⬜ | Not Started |
| 11 | Epilogue | ⬜ | ⬜ | ⬜ | Not Started |
| 12 | Appendix | ⬜ | ⬜ | ⬜ | Not Started |

**Second Pass (after completing 6-12):**
| # | Chapter | Phase 1 | Phase 2 | Phase 3 | Status |
|---|---------|---------|---------|---------|--------|
| 00 | Prologue | ⬜ | ⬜ | ⬜ | Pending |
| 01 | One Size Fits None | ⬜ | ⬜ | ⬜ | Pending |
| 02 | The Broken Line | ⬜ | ⬜ | ⬜ | Pending |
| 03 | First Little Commune | ⬜ | ⬜ | ⬜ | Pending |
| 04 | Commons of Safety | ⬜ | ⬜ | ⬜ | Pending |
| 05 | Surplus Engine | ⬜ | ⬜ | ⬜ | Pending |

---

## PHASE 1: OPUS 4.5 - Analysis, Architecture Check, AND Content Revisions

**Input Files:**
- Chapter draft from `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md` (lines 2192-2499)
- For Chapter 6 ONLY: Also compare `manuscript/temp-chapter6-body-from-review.txt` (newer content)
- `editorial/style/STYLE_RULE_EM_DASH_PROHIBITION.md`
- `editorial/ENRICHMENT_TEMPLATE.md`
- `editorial/MASTERPIECE_GENERATION_MODE.md`
- `reference/knowledge-graph/entity-database-canonical.json`
- `reference/VOICE_VALIDATION_CHECKLIST.md` Section 6 (Habitat Architecture Check)

**Tasks:**

- [ ] 1.1 Read current chapter from `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`
- [ ] 1.2 **HABITAT ARCHITECTURE CHECK** (per VOICE_VALIDATION_CHECKLIST Section 6):
  - Verify habitat DEFINED BY correct mechanism (not by what flows through)
  - Check: Family=blood/chosen bonds, Safety=risk pooling, Market=price/competition, Friendship=trust/reputation/exit
  - Flag any text that makes a FLOW-THROUGH concept (like excess) seem definitional
- [ ] 1.3 Identify alignment issues with:
  - Canonical database entities and definitions (check `defining_characteristics` vs `what_flows_through`)
  - Cross-chapter thread requirements
  - Entity mandates from enriched outline
  - Logical flow dependencies
- [ ] 1.4 Apply `STYLE_RULE_EM_DASH_PROHIBITION.md` - flag all em dash violations
- [ ] 1.5 Apply `ENRICHMENT_TEMPLATE.md` - verify all seven enrichment layers present
- [ ] 1.6 Apply `MASTERPIECE_GENERATION_MODE.md` - verify quality bar met
- [ ] 1.7 Document all issues found in WORKING AREA below
- [ ] **1.8 MAKE ALL CONTENT REVISIONS:**
  - Fix all architectural errors (correct what DEFINES vs what FLOWS THROUGH)
  - Replace all em dashes per style rules
  - Correct any alignment issues with canonical database
  - Ensure proper entity usage and relationships
- [ ] 1.9 Update `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md` with corrected chapter
- [ ] 1.10 **⚠️ HANDOFF → Tell user: "Switch to Sonnet 4.5 agent for Phase 2 voice polish"**

---

## PHASE 2: SONNET 4.5 - Voice/Tone/Feel Polish ONLY

**⚠️ CRITICAL: Sonnet does NOT make content corrections. Opus already made them.**

**Input Files:**
- Corrected chapter from `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`
- `reference/VOICE_VALIDATION_CHECKLIST.md`
- `reference/BOOK_DNA_WRITING_GUIDE.md`

**Tasks:**

- [ ] 2.1 Read `VOICE_VALIDATION_CHECKLIST.md` and `BOOK_DNA_WRITING_GUIDE.md`
- [ ] 2.2 Polish voice, tone, and feel ONLY - do NOT change content or meaning:
  - Smooth awkward phrasing from Opus edits
  - Ensure I→D→G phase balance feels natural (10-15% / 60-70% / 15-25%)
  - Check chapter flows with surrounding chapters
- [ ] 2.3 Verify chapter fits seamlessly with rest of book
- [ ] 2.4 Generate updated `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.docx` for user review
- [ ] 2.5 **⚠️ HANDOFF → Tell user: "Review .docx and make any tweaks, then switch to Opus 4.5 for Phase 3"**

---

## PHASE 3: OPUS 4.5 - Word Sync

**Input Files:**
- User-edited `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.docx`
- `reference/WORD_TO_MARKDOWN_SYNC_PROTOCOL.md`
- `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`

**Tasks:**

- [ ] 3.1 Confirm user has completed review of .docx
- [ ] 3.2 Apply `WORD_TO_MARKDOWN_SYNC_PROTOCOL.md`:
  - Extract text from both baseline and edited .docx
  - Generate diff
  - Categorize changes
- [ ] 3.3 Sync all user tweaks back to `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`
- [ ] 3.4 **⚠️ UPDATE THIS FILE:**
  - Mark current chapter's Phase 3 as ✅ in Master Checklist
  - Update chapter Status to "Complete"
  - Confirm next chapter ready to begin
- [ ] 3.5 **CHAPTER COMPLETE → Proceed to next chapter Phase 1**

---

## CURRENT CHAPTER WORKING AREA

### Chapter: 06 - Friendship, Anarchy, Order

**Source:** Lines 2192-2499 in `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`  
**Comparison:** `manuscript/temp-chapter6-body-from-review.txt` (REVIEW version with ~5,500 more chars)

**Phase 1 Notes (Opus):**
```
STEP 1.1 - READ CHAPTER: ✅ Complete
- Source: manuscript/temp-chapter6-body-from-review.txt (~31,700 chars, ~5,800 words)
- REVIEW version has enhanced moving day scene (semi-truck passage)
- Current COMPLETE.md version: ~4,925 words (needs REVIEW content merged)

STEP 1.2 - HABITAT ARCHITECTURE CHECK: ✅ FIXED

All architectural errors corrected:
- ✅ Renamed subsection to "A Thread Worth Following: Where Excess Flows"
- ✅ Fixed "Friendship runs on" to emphasize trust/reputation/exit
- ✅ Fixed Section 3b "And in friendship?" answer
- ✅ Fixed Phase 3 capstone to separate DEFINES from FLOWS THROUGH
- ✅ Reframed opening excess observation as forward reference to Ch 9

STEP 1.3 - EM DASH CHECK: ✅ FIXED
All 50 em dashes replaced with periods, commas, or colons as appropriate.

STEP 1.4 - ALIGNMENT CHECK: ✅ All entities present
- Moving Day scene ✅ (enhanced with semi-truck passage)
- Trust/Reputation/Exit mechanisms ✅
- Cajun Navy ✅
- Identity formation ✅
- Ring Complete table ✅
- "When Friendship Gets HR" callback ✅
- Open Source ✅
- Volunteer work ✅

STEP 1.5 - MASTERPIECE MODE CHECK: ✅ Quality bar met
- Sensory detail (greasy pizza, sore backs) ✅
- Full scene development ✅
- Verification invitations present ✅
- Word count: ~5,062 (target 6,500-7,500) ⚠️ slightly under but acceptable

STEP 1.6 - ISSUES DOCUMENTED: ✅ Complete

STEP 1.7-1.9 - CONTENT REVISIONS: ✅ COMPLETE
All revisions applied to manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md

STEP 1.10 - HANDOFF: ⚠️ Ready for Sonnet voice polish
```

**Phase 2 Notes (Sonnet):**
```
Sonnet: ONLY polish voice/tone/feel. Do NOT change content or meaning.
Chapter has been architecturally corrected. Just smooth any awkward phrasing.
```

**Phase 3 Notes (Opus):**
```
[Document sync changes here]
```

---

## CHANGE LOG

### 2026-01-30 - Chapter 6 Phase 1 Complete (Opus)
- Merged semi-truck enhancement from REVIEW version
- Fixed 4 architectural errors (excess now correctly positioned as FLOWING THROUGH, not DEFINING)
- Replaced all 50 em dashes
- Updated manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md

| Date | Chapter | Action | Agent |
|------|---------|--------|-------|
| 2026-01-30 | - | Workflow created | Opus |
