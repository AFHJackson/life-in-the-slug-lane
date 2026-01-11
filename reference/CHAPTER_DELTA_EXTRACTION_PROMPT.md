# CHAPTER DELTA EXTRACTION PROMPT
## For Opus 4.5 - Delta Extraction Mode

**Version:** 1.0  
**Date:** January 11, 2026  
**Use:** For Chapters 1+ (after Prologue canonical established)

---

## PASTE THIS INTO OPUS 4.5 CHAT:

```markdown
TASK: Delta Extraction - Chapter [X] - Identify Changes Against Canonical Database

I need you to extract ONLY the changes (deltas) that Chapter [X] makes relative to our canonical entity database. This is fundamentally different from full extraction.

---

## CRITICAL: YOU ARE EXTRACTING DELTAS, NOT FULL ENTITIES

**DO NOT re-extract entities that already exist in canonical database.**

**ONLY extract:**
1. **UPDATES** - How chapter refines existing canonical entities
2. **ADDITIONS** - Entities that are NEW (not in canonical)
3. **CONTRADICTIONS** - Where chapter conflicts with canonical definitions

---

## REQUIRED READING FIRST

**You MUST read these guides before extracting:**
1. `reference/DELTA_EXTRACTION_GUIDE.md` (complete delta process)
2. `reference/knowledge-graph/entity-database-canonical.json` (what already exists)
3. `reference/KNOWLEDGE_SCHEMA.md` (schema structure)

**Read all three now, then confirm you've reviewed them before proceeding.**

---

## CANONICAL DATABASE AWARENESS

**The canonical database currently contains:**
- All entities from Prologue
- [List any previous chapter merges if applicable]

**Before extracting, familiarize yourself with:**
- Which entities already exist
- Current definitions of each
- Current examples and relationships

**Your job:** Identify what THIS chapter ADDS or CHANGES.

---

## THREE EXTRACTION CATEGORIES

### Category 1: UPDATES

**Extract when:**
- Chapter adds examples to existing canonical concept
- Chapter clarifies existing canonical definition
- Chapter shows new application of existing framework
- Chapter refines or extends existing entity

**DO NOT extract:**
- Mere mentions of canonical entities (no new information)
- Restating what's already in canonical

**Schema:**
```json
{
  "entity_name": "[Existing canonical entity name - EXACT match]",
  "update_type": "example_added | clarification | refinement | new_application | relationship_extended",
  "canonical_current": "[Current definition from canonical database]",
  "chapter_contribution": "[SPECIFICALLY what this chapter adds]",
  "proposed_merge": "[HOW to integrate into canonical]",
  "location": "Chapter X, paragraph Y",
  "confidence": "high | medium | low"
}
```

---

### Category 2: ADDITIONS

**Extract when:**
- Entity is completely new (not in canonical database)
- Framework first introduced in this chapter
- New example or story
- New relationship not previously documented

**CRITICAL CHECK:**
Before extracting as ADDITION, verify:
- ✅ Searched canonical database thoroughly
- ✅ Checked aliases and similar concepts
- ✅ This is genuinely new, not overlooked in Prologue

**Schema:**
```json
{
  "entity_name": "[New entity name]",
  "type": "framework | concept | principle | mechanism | example",
  "definition": "[Complete definition]",
  "definition_type": "technical_standard | book_coined | book_original",
  
  // Type-specific fields per KNOWLEDGE_SCHEMA.md
  // If technical_standard: add source, book_usage
  // If book_coined: add builds_on
  // If book_original: add components, purpose
  
  "why_new": "[Explanation: Why not in Prologue? Genuinely new or overlooked?]",
  "first_mention": "Chapter X, paragraph Y",
  "relates_to_canonical": ["List existing canonical entities"],
  "integration_recommendation": "add_to_canonical | merge_with_existing | flag_for_review"
}
```

---

### Category 3: CONTRADICTIONS

**Extract when:**
- Chapter defines entity differently than canonical
- Chapter uses entity in way that conflicts with canonical
- Example contradicts canonical framework
- Relationship conflicts with canonical map

**Schema:**
```json
{
  "entity_name": "[Entity with contradiction]",
  "canonical_definition": "[Definition from canonical database - EXACT quote]",
  "chapter_definition": "[Conflicting definition in this chapter - EXACT quote]",
  "conflict_type": "definition | usage | example | relationship",
  "severity": "critical | moderate | minor",
  "location": "Chapter X, paragraph Y",
  "analysis": "[Your analysis of the conflict]",
  "resolution_options": [
    "Keep canonical (chapter is wrong/imprecise)",
    "Update canonical (chapter improves it)",
    "Merge both (synthesis possible)",
    "Flag for manuscript revision (genuine contradiction)"
  ],
  "recommendation": "[Your recommended resolution with reasoning]"
}
```

---

## DECISION TREE FOR EVERY ENTITY IN CHAPTER

```
Does this entity exist in canonical database?
│
├─ YES → Does chapter add new information?
│         │
│         ├─ YES → Extract as UPDATE
│         └─ NO → Don't extract (mere mention)
│
│         Does chapter contradict canonical?
│         │
│         └─ YES → Extract as CONTRADICTION
│
└─ NO → Extract as ADDITION
         (But verify it's truly new first!)
```

---

## EXTRACTION PROCESS

### Step 1: Review Canonical Database (10 minutes)

**Open:** `reference/knowledge-graph/entity-database-canonical.json`

**Note:**
- All entity names currently in database
- Key definitions
- Current examples and relationships

**Keep canonical open for reference throughout extraction.**

---

### Step 2: Read Chapter Completely (First Pass)

**Read chapter start to finish WITHOUT extracting yet.**

**Mark:**
- Which canonical entities appear
- What seems new
- What seems contradictory
- Potential updates

---

### Step 3: Systematic Delta Extraction (Second Pass)

**3a. Extract UPDATES first**
- For each canonical entity mentioned
- Does chapter add examples? → UPDATE
- Does chapter clarify? → UPDATE
- Does chapter show new application? → UPDATE
- Just mentioned in passing? → Don't extract

**3b. Extract ADDITIONS second**
- For each concept not in canonical
- Verify it's truly new (search canonical thoroughly)
- Extract complete entity per schema
- Explain why it's new

**3c. Extract CONTRADICTIONS last**
- For each canonical entity used
- Does chapter define differently? → CONTRADICTION
- Does usage conflict? → CONTRADICTION
- Do examples contradict? → CONTRADICTION

---

### Step 4: Self-Validation

**Before finalizing, verify:**
- [ ] Every UPDATE cites correct canonical entity
- [ ] Every UPDATE has specific chapter contribution (not vague)
- [ ] Every UPDATE has proposed merge
- [ ] Every ADDITION is truly new (checked canonical)
- [ ] Every ADDITION has complete definition per schema
- [ ] Every ADDITION explains why it's new
- [ ] Every CONTRADICTION cites both definitions exactly
- [ ] Every CONTRADICTION has severity and recommendation
- [ ] All locations are precise (chapter, paragraph)

---

## OUTPUT FORMAT

**File:** `editorial/extractions/deltas/chapter-[##]-delta.json`

**Structure:**
```json
{
  "source_file": "manuscript/03-chapter-1.md",
  "extraction_date": "2026-01-11",
  "extractor": "opus-4.5",
  "canonical_reference": "reference/knowledge-graph/entity-database-canonical.json",
  "canonical_version": "After Prologue merge",
  
  "updates": [
    {
      "entity_name": "Scale Errors",
      "update_type": "example_added",
      "canonical_current": "The mistake of applying a system designed for one scale to a different scale",
      "chapter_contribution": "Adds concrete example: Family forced to operate like business destroys intimacy",
      "proposed_merge": "Add to examples array: 'Family as business (Ch 1, para 8)'",
      "location": "Chapter 1, paragraph 8",
      "confidence": "high"
    }
    // ... more updates
  ],
  
  "additions": [
    {
      "entity_name": "The Broken Line",
      "type": "metaphor",
      "definition": "The traditional left/right political spectrum that fails to capture multi-dimensional reality",
      "definition_type": "book_coined",
      "builds_on": "Common 'left/right' political terminology",
      "purpose": "Explains why binary political thinking is inadequate",
      "why_new": "Chapter 1 introduces this as contrast to The Ring model (not present in Prologue)",
      "first_mention": "Chapter 1, paragraph 3",
      "relates_to_canonical": ["The Ring", "System of Systems"],
      "integration_recommendation": "add_to_canonical"
    }
    // ... more additions
  ],
  
  "contradictions": [
    {
      "entity_name": "Capitalism",
      "canonical_definition": "System optimized for surplus generation through exchange at population scale",
      "chapter_definition": "Chapter describes it as 'pure selfishness' (paragraph 22)",
      "conflict_type": "definition",
      "severity": "moderate",
      "location": "Chapter 1, paragraph 22",
      "analysis": "Chapter oversimplifies capitalism for rhetorical effect. Conflicts with canonical nuanced definition.",
      "resolution_options": [
        "Keep canonical (chapter is oversimplified)",
        "Flag for manuscript revision (clarify language)"
      ],
      "recommendation": "Keep canonical definition, flag paragraph 22 for revision to avoid oversimplification"
    }
    // ... more contradictions
  ],
  
  "summary": {
    "total_updates": 0,
    "total_additions": 0,
    "total_contradictions": 0,
    "high_confidence_updates": 0,
    "additions_recommended_for_canonical": 0,
    "critical_contradictions": 0,
    "moderate_contradictions": 0,
    "minor_contradictions": 0
  },
  
  "extraction_notes": {
    "chapter_themes": "[Main themes or focuses of this chapter]",
    "canonical_entities_referenced": ["array of canonical entities mentioned"],
    "entities_merely_mentioned": ["canonical entities mentioned but no delta extracted"],
    "quality_concerns": ["any extraction issues or uncertainties"],
    "reviewer_attention_needed": ["items requiring Joshua's decision]"
  }
}
```

---

## QUALITY EXAMPLES

### GOOD UPDATE ✅

```json
{
  "entity_name": "Four Habitats",
  "update_type": "clarification",
  "canonical_current": "Four distinct scales of human relationship where different systems operate naturally",
  "chapter_contribution": "Clarifies that we don't choose one habitat - we move through all four continuously, not exclusively",
  "proposed_merge": "Add to definition: 'Humans navigate all four continuously, not exclusively.'",
  "location": "Chapter 1, paragraph 15",
  "confidence": "high"
}
```

**Why good:**
- References exact canonical definition
- States specific contribution
- Proposes clear merge
- Precise location

---

### BAD UPDATE ❌

```json
{
  "entity_name": "Four Habitats",
  "update_type": "mentioned",
  "chapter_contribution": "Chapter mentions Four Habitats"
}
```

**Why bad:**
- Mere mention, not an update
- No canonical reference
- No specific contribution
- No proposed merge
- Vague

---

### GOOD ADDITION ✅

```json
{
  "entity_name": "The Broken Line",
  "type": "metaphor",
  "definition": "The traditional left/right political spectrum that fails to capture the multi-dimensional reality of political systems",
  "definition_type": "book_coined",
  "builds_on": "Common 'left/right' political terminology",
  "purpose": "Explains why binary political thinking is inadequate and why The Ring is needed",
  "why_new": "First introduced in Chapter 1 as explicit contrast to The Ring. Not present in Prologue which focused on establishing The Ring itself.",
  "first_mention": "Chapter 1, paragraph 3",
  "relates_to_canonical": ["The Ring", "System of Systems"],
  "integration_recommendation": "add_to_canonical"
}
```

**Why good:**
- Complete entity per schema
- Clear explanation of why new
- Shows relationships
- Integration recommendation

---

### BAD ADDITION ❌

```json
{
  "entity_name": "Left/Right",
  "definition": "Political spectrum"
}
```

**Why bad:**
- Might already be in canonical (didn't check)
- Incomplete definition
- No definition_type
- No explanation of why new
- Missing required fields

---

### GOOD CONTRADICTION ✅

```json
{
  "entity_name": "Capitalism",
  "canonical_definition": "System optimized for surplus generation through exchange at population scale",
  "chapter_definition": "Pure selfishness (Chapter 5, paragraph 22)",
  "conflict_type": "definition",
  "severity": "moderate",
  "location": "Chapter 5, paragraph 22",
  "analysis": "Chapter uses simplistic definition for rhetorical impact. Technically inaccurate and conflicts with canonical's more nuanced understanding that acknowledges surplus generation as distinct from pure greed.",
  "resolution_options": [
    "Keep canonical (more accurate and nuanced)",
    "Flag for manuscript revision (clarify chapter language)",
    "Update canonical (if chapter is actually better)",
    "Synthesize both (if both have merit)"
  ],
  "recommendation": "Keep canonical definition. Flag paragraph 22 for revision - soften rhetoric or add nuance to avoid misleading readers about capitalism's actual mechanisms."
}
```

**Why good:**
- Both definitions cited exactly
- Conflict clearly identified
- Severity assessed
- Multiple options considered
- Clear recommendation with reasoning

---

## SPECIAL CASES

### Case 1: Uncertain if New or Overlooked

**Situation:** Entity seems new but might have been implicit in Prologue

**Action:**
```json
{
  "entity_name": "...",
  "why_new": "Uncertain - may have been implicit in Prologue. Explicitly named for first time in this chapter.",
  "integration_recommendation": "flag_for_review"
}
```

---

### Case 2: Multiple Updates to Same Entity

**Situation:** Chapter adds 3 examples to "Scale Errors"

**Action:** Create ONE UPDATE object with all contributions
```json
{
  "entity_name": "Scale Errors",
  "update_type": "multiple_examples_added",
  "chapter_contribution": "Adds three examples: (1) Family forced into market logic, (2) Market efficiency applied to safety commons, (3) Socialist planning imposed on voluntary networks",
  "proposed_merge": "Add all three to examples array in canonical"
}
```

---

### Case 3: Borderline Contradiction

**Situation:** Definitions are close but slightly different

**Decision:**
```
Is difference substantive?
├─ YES → CONTRADICTION (could confuse readers)
└─ NO → UPDATE with type "refinement" (just clearer wording)
```

---

## VALIDATION CHECKLIST

**Before submitting delta extraction:**

- [ ] Canonical database reviewed thoroughly before extracting
- [ ] All UPDATES reference existing canonical entities
- [ ] All UPDATES state specific contributions (not vague)
- [ ] All UPDATES have proposed merge actions
- [ ] All ADDITIONS verified as genuinely new
- [ ] All ADDITIONS have complete definitions per schema
- [ ] All ADDITIONS explain why they're new
- [ ] All CONTRADICTIONS cite both definitions exactly
- [ ] All CONTRADICTIONS have severity + recommendation
- [ ] Summary counts are accurate
- [ ] Extraction notes complete
- [ ] No mere mentions extracted as updates
- [ ] Self-validation performed

---

## DELIVERABLE

**Create:** `editorial/extractions/deltas/chapter-[##]-delta.json`

**Then provide summary report:**

```markdown
# CHAPTER [X] DELTA EXTRACTION COMPLETE

## Extraction Summary
- **Updates:** [number] ([high/medium/low confidence breakdown])
- **Additions:** [number] ([recommended for canonical/merge/review])
- **Contradictions:** [number] ([critical/moderate/minor breakdown])

## Key Findings

### Notable Updates
- [Entity]: [Brief description of update]

### New Entities
- [Entity]: [Brief description]

### Contradictions Flagged
- [Entity]: [Brief description of conflict]

## Canonical Entities Referenced
[List of canonical entities this chapter engaged with]

## Canonical Entities Not Mentioned
[Notable canonical entities absent from this chapter]

## Quality Notes
- Confidence level: [Overall assessment]
- Concerns: [Any extraction uncertainties]
- Reviewer attention: [Items needing Joshua's decision]

## Readiness for Merge
[Ready / Needs Review / Issues Found]

---

**Next step:** Joshua reviews delta using MERGE_PROTOCOL.md and integrates approved changes into canonical database.
```

---

## BEGIN DELTA EXTRACTION

**Step 1: Confirm you've read required guides**
- [ ] DELTA_EXTRACTION_GUIDE.md
- [ ] entity-database-canonical.json (current canonical)
- [ ] KNOWLEDGE_SCHEMA.md

**Step 2: Review canonical database**
- Familiarize with existing entities
- Note current definitions
- Keep canonical open for reference

**Step 3: Read chapter completely (first pass)**
- Note canonical entities referenced
- Note potential updates/additions/contradictions
- Don't extract yet

**Step 4: Systematic delta extraction (second pass)**
- Extract UPDATES
- Extract ADDITIONS
- Extract CONTRADICTIONS

**Step 5: Self-validate**
- Check all required fields present
- Verify no mere mentions extracted
- Ensure precise locations

**Step 6: Create delta JSON**
- Save to: `editorial/extractions/deltas/chapter-[##]-delta.json`

**Step 7: Provide summary report**

---

**Ready to begin? Confirm you've read the guides, then start with Chapter [X].**
```

---

## USAGE NOTES FOR HUMAN COORDINATOR

**When using this prompt:**
1. Replace `[X]` with actual chapter number
2. Replace `[##]` in file paths with zero-padded number (e.g., `01`)
3. Specify which chapter manuscript file to process
4. Verify canonical database is current before Opus begins

**Expected Opus workflow:**
1. Reads delta extraction guide
2. Reads canonical database (familiarizes)
3. Reads knowledge schema
4. Confirms understanding
5. Processes chapter systematically
6. Creates delta JSON
7. Provides summary report

**Time estimate:** 30-60 minutes per chapter depending on complexity

---

**This prompt enables delta extraction against the growing canonical database, preventing concept drift and ensuring clean knowledge graph evolution.**
