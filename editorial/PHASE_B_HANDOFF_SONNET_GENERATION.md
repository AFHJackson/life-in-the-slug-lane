# PHASE B HANDOFF: Opus → Sonnet Chapter Generation

**Date:** January 20, 2026  
**From:** Opus 4.5 (Enrichment Agent)  
**To:** Sonnet 4.5 (Generation Agent)  
**Status:** Phase A COMPLETE - Ready for Phase B

---

## EXECUTIVE SUMMARY

Opus has completed Phase A enrichment of all 13 chapter outlines. Each outline now contains seven enrichment layers providing complete specification for Sonnet to generate chapters autonomously.

**The Workflow:**
- **Phase A (COMPLETE):** Opus enriches all outlines with cross-chapter coherence
- **Phase B (NOW):** Sonnet generates all chapters from enriched outlines
- **Phase C (AFTER B):** Opus validates generated chapters

---

## WHAT OPUS HAS PREPARED

### Enriched Outlines Location
All enriched outlines are in: `editorial/outlines/enriched/`

### The Seven Layers (in each outline)

Every enriched outline contains:

1. **Layer 1: Cross-Chapter Thread Mapping**
   - What threads this chapter RECEIVES (from prior chapters)
   - What threads this chapter PLANTS (for later chapters)
   - What threads this chapter MUST NOT USE (scope discipline)
   - Elegant Emergence notes (why this matters)

2. **Layer 2: Entity Mandates**
   - Entities that MUST appear (with canonical definitions)
   - Entities that MUST NOT appear (save for other chapters)
   - Terminology precision requirements

3. **Layer 3: Logical Flow Dependencies**
   - Preconditions (what reader must already know)
   - Internal logic chain (how sections build)
   - Verification chain (what each verification tests)

4. **Layer 4: Voice Constraints**
   - Phase-specific tone (I/D/G percentages and targets)
   - Forbidden patterns (with ✅ alternatives)
   - Required patterns

5. **Layer 5: Example Specifications**
   - Mandatory scene elements for each major story
   - Key passages that MUST appear
   - Emotional beats to hit

6. **Layer 6: Transition Requirements**
   - Into chapter (from previous)
   - Between sections (internal bridges)
   - Out of chapter (to next)

7. **Layer 7: Generation Constraints**
   - Word count targets per phase
   - Structural requirements (checklist)
   - Anti-patterns to avoid
   - Quality markers
   - Validation checklist (for Opus post-generation)

---

## SONNET'S TASK

### For Each Chapter:

1. **Read the enriched outline COMPLETELY**
   - All seven layers
   - Key passages in Cross-Reference section

2. **Generate chapter following all specifications**
   - Hit word count targets
   - Include all required entities
   - Follow voice constraints per phase
   - Use verification invitations as specified
   - Hit all transition requirements

3. **Save generated chapter to:** `manuscript/generated/XX-chapter-name-GENERATED.md`

### Generation Order

Generate in order (threads build on each other):

| Order | Chapter | Enriched Outline |
|-------|---------|------------------|
| 1 | Prologue | 00-prologue-outline-ENRICHED.md |
| 2 | Chapter 1 | 01-one-size-fits-none-outline-ENRICHED.md |
| 3 | Chapter 2 | 02-broken-line-outline-ENRICHED.md |
| 4 | Chapter 3 | 03-first-little-commune-outline-ENRICHED.md |
| 5 | Chapter 4 | 04-commons-of-safety-outline-ENRICHED.md |
| 6 | Chapter 5 | 05-surplus-engine-outline-ENRICHED.md |
| 7 | Chapter 6 | 06-friendship-anarchy-order-outline-ENRICHED.md |
| 8 | Chapter 7 | 07-when-systems-touch-outline-ENRICHED.md |
| 9 | Chapter 8 | 08-ring-compass-outline-ENRICHED.md |
| 10 | Chapter 9 | 09-obligation-to-excess-outline-ENRICHED.md |
| 11 | Chapter 10 | 10-stewardship-outline-ENRICHED.md |
| 12 | Epilogue | 11-epilogue-outline-ENRICHED.md |
| 13 | Appendix | 12-appendix-outline-ENRICHED.md |

---

## CRITICAL SPECIFICATIONS

### Voice Architecture (I→D→G)

| Phase | Target % | Voice | Purpose |
|-------|----------|-------|---------|
| I (Invention) | 10-15% | Story, curiosity, felt experience | "I recognize this" |
| D (Discernment) | 60-70% | Testing, verification, limits | "I can verify this" |
| G (Galvanizing) | 15-25% | Recognition, equipment, rally | "Now I'm ready to act" |

### Key Voice Rules

**In Galvanizing Phase:**
- ❌ NEVER "You should..." / "You need to..." / "Make sure you..."
- ✅ ALWAYS "You'll now recognize..." / "You can see..." / "This will happen because..."
- Recognition language, NOT prescription

**Verification Invitations:**
- Must have 4-6 per chapter in Discernment phase
- Each should test a specific recognition
- Format: "Think about [reader's own experience]. What do you notice?"

**Limits Acknowledged:**
- Every Discernment phase includes honest limits
- "This doesn't solve everything, but..."
- Shows intellectual humility

### Key Passages

Each enriched outline has a "CROSS-REFERENCE: KEY PASSAGES FOR SONNET" section. These passages MUST appear (or be closely paraphrased) in the generated chapter.

---

## NEW CONTENT SOURCES

For chapters with new content, use these files:

| Chapter | New Content File |
|---------|------------------|
| Ch 3 | `reference/new-content/new-content-ch3-family-dinner.md` |
| Ch 9 | `reference/new-content/new-content-ch9-malia-excess.md` |
| Ch 10 | `reference/new-content/new-content-ch10-matt-navigator.md` |
| Epilogue | `reference/new-content/new-content-epilogue-vision.md` |
| Appendix | `reference/new-content/new-content-appendix-25-years.md` |

---

## ENTITY DATABASE

Canonical definitions for all entities are in:
`reference/knowledge-graph/entity-database-canonical.json`

When an enriched outline references an entity, use the canonical definition from the database.

---

## AFTER GENERATION

After Sonnet generates each chapter:

1. **Self-check against Layer 7 checklist** in enriched outline
2. **Note any deviations** in a comment at end of generated file
3. **Flag for Opus validation** if uncertain about any specification

Opus will run Phase C validation after all chapters are generated.

---

## OUTPUT FORMAT

Each generated chapter should:

1. **Start with header:**
```markdown
# [CHAPTER TITLE]
## Generated from Enriched Outline

**Generated:** [Date]
**Word Count:** [Actual count]
**Target:** [From outline]
**Phase Breakdown:** I: X% / D: Y% / G: Z%
```

2. **Use clear section headers** matching outline phases

3. **End with self-check:**
```markdown
---
## GENERATION NOTES

**Structural Requirements Met:**
- [x] Item from Layer 7 checklist
- [x] Item from Layer 7 checklist
- [ ] Any items needing Opus review

**Deviations from Outline:**
- None / or list any

**Flags for Opus:**
- None / or list any
```

---

## READY TO BEGIN

Phase A enrichment is complete. All 13 outlines are enriched with seven layers each. Cross-chapter threads are mapped for total cohesion.

**Sonnet can now generate chapters in order, starting with Prologue.**

---

**END OF HANDOFF DOCUMENT**
