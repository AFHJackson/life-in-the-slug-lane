# CHAPTER POLISH WORKFLOW
## Per-Chapter Refinement Protocol

**Purpose:** Systematic polish of each chapter through Opus→Sonnet→Opus workflow  
**Created:** January 30, 2026  
**Status:** Active - First Pass (Chapters 6-12)

---

## WORKFLOW OVERVIEW

```
OPUS 4.5: Analysis & Enrichment Check
    ↓
SONNET 4.5: Voice Correction & Integration
    ↓
OPUS 4.5: Word Sync from User Review
    ↓
UPDATE THIS CHECKLIST → Next Chapter
```

---

## MASTER CHECKLIST - FIRST PASS

| # | Chapter | Phase 1 (Opus) | Phase 2 (Sonnet) | Phase 3 (Opus) | Status |
|---|---------|----------------|------------------|----------------|--------|
| 06 | Friendship, Anarchy, Order | ⬜ | ⬜ | ⬜ | Not Started |
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

## PHASE 1: OPUS 4.5 - Analysis & Enrichment Check

**Input Files:**
- Chapter draft from `manuscript/generated/`
- `editorial/style/STYLE_RULE_EM_DASH_PROHIBITION.md`
- `editorial/ENRICHMENT_TEMPLATE.md`
- `editorial/MASTERPIECE_GENERATION_MODE.md`
- `reference/knowledge-graph/entity-database-canonical.json`

**Tasks:**

- [ ] 1.1 Read current chapter draft from `manuscript/generated/[##-chapter-name]-GENERATED-FULL.md`
- [ ] 1.2 Identify all direct and indirect issues with chapter's alignment and implementation of:
  - Canonical database entities and definitions
  - Cross-chapter thread requirements
  - Entity mandates from enriched outline
  - Logical flow dependencies
- [ ] 1.3 Apply `STYLE_RULE_EM_DASH_PROHIBITION.md` - flag all em dash violations
- [ ] 1.4 Apply `ENRICHMENT_TEMPLATE.md` - verify all seven enrichment layers present
- [ ] 1.5 Apply `MASTERPIECE_GENERATION_MODE.md` - verify quality bar met:
  - Word count at maximum of range
  - Full scene development
  - Sensory immersion
  - Verification invitations with real space
- [ ] 1.6 Document all issues found in handoff notes for Sonnet
- [ ] 1.7 **⚠️ HANDOFF → Tell user: "Switch to Sonnet 4.5 agent for Phase 2"**

---

## PHASE 2: SONNET 4.5 - Voice Correction & Integration

**Input Files:**
- Issues documented by Opus in Phase 1
- `reference/VOICE_VALIDATION_CHECKLIST.md`
- `reference/BOOK_DNA_WRITING_GUIDE.md`
- `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`

**Tasks:**

- [ ] 2.1 Read `VOICE_VALIDATION_CHECKLIST.md` and `BOOK_DNA_WRITING_GUIDE.md`
- [ ] 2.2 Correct voice, tone, and feel while:
  - Preserving all insights and meaning
  - Maintaining chapter's job in the book's argument
  - Ensuring I→D→G phase balance (10-15% / 60-70% / 15-25%)
- [ ] 2.3 Verify chapter fits seamlessly with all other chapters
- [ ] 2.4 Insert polished chapter into `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.md`
- [ ] 2.5 Generate updated `manuscript/COMPLETE-MANUSCRIPT-FOR-REVIEW.docx` for user review
- [ ] 2.6 **⚠️ HANDOFF → Tell user: "Review .docx and make any tweaks, then switch to Opus 4.5 for Phase 3"**

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

### Chapter: [FILL IN WHEN STARTING]

**Phase 1 Notes (Opus):**
```
[Document issues found here]
```

**Phase 2 Notes (Sonnet):**
```
[Document corrections made here]
```

**Phase 3 Notes (Opus):**
```
[Document sync changes here]
```

---

## CHANGE LOG

| Date | Chapter | Action | Agent |
|------|---------|--------|-------|
| 2026-01-30 | - | Workflow created | Opus |
