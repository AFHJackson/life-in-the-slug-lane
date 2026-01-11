# DELTA EXTRACTION GUIDE
**Purpose:** Extract changes from each chapter relative to the canonical entity database  
**Version:** 1.0  
**Date:** January 11, 2026

---

## OVERVIEW

**Delta extraction is fundamentally different from full extraction.**

Instead of extracting all entities in a chapter, we extract only:
1. **UPDATES** - Refinements to existing canonical entities
2. **ADDITIONS** - New entities not in canonical database
3. **CONTRADICTIONS** - Conflicts with canonical definitions

**Goal:** Build the canonical database chapter by chapter without creating competing definitions.

---

## WHY DELTA EXTRACTION?

### The Problem with Full Extraction Per Chapter
```
Prologue defines: "System of Systems is X"
Chapter 1 defines: "System of Systems is Y" 
Chapter 2 defines: "System of Systems is Z"

→ Three competing definitions
→ No clear canonical version
→ Concept drift and confusion
```

### The Delta Extraction Solution
```
Prologue defines: "System of Systems is X" [CANONICAL]
Chapter 1 adds: "Examples: A, B, C" [UPDATE to canonical]
Chapter 2 refines: "Also applies to networks" [UPDATE to canonical]

→ One evolving canonical definition
→ Clear growth trajectory
→ No competing versions
```

---

## THREE EXTRACTION CATEGORIES

### Category 1: UPDATES

**What qualifies as an UPDATE:**
- Chapter adds examples to existing concept
- Chapter clarifies or refines existing definition
- Chapter shows new application of existing framework
- Chapter extends existing relationship
- Concept evolution without contradiction

**What to extract:**
```json
{
  "entity_name": "Scale Errors",
  "update_type": "example_added | clarification | refinement | new_application | relationship_extended",
  "canonical_current": "[current definition from canonical database]",
  "chapter_contribution": "[what this chapter adds]",
  "proposed_merge": "[how to integrate into canonical]",
  "location": "Chapter X, paragraph Y",
  "confidence": "high | medium | low"
}
```

**Examples:**

**UPDATE: Example Added**
```json
{
  "entity_name": "Four Habitats",
  "update_type": "example_added",
  "canonical_current": "Four distinct scales of human relationship where different systems operate naturally",
  "chapter_contribution": "Chapter 3 demonstrates family habitat with 'from each according to ability, to each according to need' operating naturally in household chores",
  "proposed_merge": "Add to examples array: 'Household chores distribution (Ch 3)'",
  "location": "Chapter 3, paragraphs 8-12",
  "confidence": "high"
}
```

**UPDATE: Clarification**
```json
{
  "entity_name": "The Ring",
  "update_type": "clarification",
  "canonical_current": "Circular model showing four overlapping systems",
  "chapter_contribution": "Chapter 1 clarifies that 'overlapping' means we move through all four systems continuously, not choose one",
  "proposed_merge": "Add clarification note: 'Movement is continuous and simultaneous, not sequential choice'",
  "location": "Chapter 1, paragraph 15",
  "confidence": "high"
}
```

---

### Category 2: ADDITIONS

**What qualifies as an ADDITION:**
- Completely new entity not in canonical database
- New framework introduced for first time
- New example or story
- New relationship between entities

**What to extract:**
```json
{
  "entity_name": "[New entity name]",
  "type": "framework | concept | principle | mechanism | example",
  "definition": "[Complete definition]",
  "definition_type": "technical_standard | book_coined | book_original",
  
  // Type-specific fields as per KNOWLEDGE_SCHEMA.md
  
  "why_new": "[Explanation: Why wasn't this in Prologue? Is it genuinely new or was it overlooked?]",
  "first_mention": "Chapter X, paragraph Y",
  "relates_to_canonical": ["List of existing canonical entities this connects to"],
  "integration_recommendation": "add_to_canonical | merge_with_existing | flag_for_review"
}
```

**Examples:**

**ADDITION: New Concept**
```json
{
  "entity_name": "Obligation to Excess",
  "type": "principle",
  "definition": "The internal recognition that when surplus becomes excess, we have a choice between discovery and generosity",
  "definition_type": "book_original",
  "purpose": "Explains why humans go beyond pure self-interest even when economic incentive disappears",
  "why_new": "Introduced in Chapter 5 after establishing surplus mechanism in Chapter 4. Builds on economic foundations laid earlier.",
  "first_mention": "Chapter 5, paragraph 18",
  "relates_to_canonical": ["Surplus → Excess mechanism", "Homo Economicus", "Witching Hour"],
  "integration_recommendation": "add_to_canonical"
}
```

**ADDITION: New Example**
```json
{
  "entity_name": "Maya's Hospital",
  "type": "story_example",
  "description": "Healthcare worker navigating all four habitats within hospital system",
  "illustrates": ["Four Habitats", "Scale Errors", "System of Systems"],
  "why_new": "Chapter 7 introduces workplace examples of habitat navigation",
  "first_mention": "Chapter 7, opening story",
  "usage_pattern": "recurring",
  "relates_to_canonical": ["Four Habitats", "Slug Line"],
  "integration_recommendation": "add_to_canonical"
}
```

---

### Category 3: CONTRADICTIONS

**What qualifies as a CONTRADICTION:**
- Chapter defines entity differently than canonical
- Chapter uses entity in way that conflicts with canonical usage
- Example contradicts canonical framework
- Relationship conflicts with canonical relationship map

**What to extract:**
```json
{
  "entity_name": "[Entity that has contradiction]",
  "canonical_definition": "[Definition from canonical database]",
  "chapter_definition": "[Conflicting definition in this chapter]",
  "conflict_type": "definition | usage | example | relationship",
  "severity": "critical | moderate | minor",
  "location": "Chapter X, paragraph Y",
  "analysis": "[Your analysis of the conflict]",
  "resolution_options": [
    "Keep canonical (chapter is wrong)",
    "Update canonical (chapter improves it)",
    "Merge both (synthesis possible)",
    "Flag for manuscript revision (genuine contradiction)"
  ],
  "recommendation": "[Your recommended resolution]"
}
```

**Examples:**

**CONTRADICTION: Definition Conflict**
```json
{
  "entity_name": "Capitalism",
  "canonical_definition": "System optimized for surplus generation through exchange at population scale",
  "chapter_definition": "Pure self-interest maximization",
  "conflict_type": "definition",
  "severity": "moderate",
  "location": "Chapter 5, paragraph 3",
  "analysis": "Chapter oversimplifies capitalism as pure greed. Conflicts with canonical which acknowledges surplus generation as distinct from pure selfishness.",
  "resolution_options": [
    "Keep canonical (chapter is sloppy)",
    "Flag for manuscript revision (need clarification)"
  ],
  "recommendation": "Keep canonical, flag paragraph for revision to avoid misleading readers"
}
```

**CONTRADICTION: Usage Conflict**
```json
{
  "entity_name": "Four Habitats",
  "canonical_definition": "We move through all four continuously",
  "chapter_definition": "Chapter 2 suggests we 'choose which habitat to operate in'",
  "conflict_type": "usage",
  "severity": "critical",
  "location": "Chapter 2, paragraph 22",
  "analysis": "Chapter language suggests voluntary choice of habitat. Contradicts canonical framework that we're always in all four.",
  "resolution_options": [
    "Keep canonical (chapter language is imprecise)",
    "Flag for manuscript revision (needs rewording)"
  ],
  "recommendation": "Flag for manuscript revision - this could confuse readers about core framework"
}
```

---

## EXTRACTION WORKFLOW

### Step 1: Load Canonical Database

**Before extracting from any chapter:**
1. Open `reference/knowledge-graph/entity-database-canonical.json`
2. Review all entities currently in canonical
3. Note key definitions and relationships
4. Keep canonical open for reference during extraction

---

### Step 2: Read Chapter Completely

**First pass:**
- Read chapter start to finish
- Don't extract yet, just note:
  - Which canonical entities appear
  - What seems new
  - What seems contradictory

---

### Step 3: Systematic Delta Extraction

**Second pass - Extract in order:**

**3a. Identify UPDATES first**
- For each canonical entity mentioned in chapter
- Does chapter add examples?
- Does chapter clarify meaning?
- Does chapter show new application?
- If yes → Extract as UPDATE

**3b. Identify ADDITIONS second**
- For each concept/example in chapter
- Is it in canonical database?
- If no → Extract as ADDITION
- If unsure → Flag for review

**3c. Identify CONTRADICTIONS last**
- For each canonical entity mentioned
- Does chapter define it differently?
- Does chapter use it inconsistently?
- Do examples contradict framework?
- If yes → Extract as CONTRADICTION

---

### Step 4: Self-Validation

**Before finalizing, check:**
- [ ] Every UPDATE references correct canonical entity
- [ ] Every ADDITION explains why it's new
- [ ] Every CONTRADICTION has both definitions cited
- [ ] All extractions have clear locations (chapter, paragraph)
- [ ] Proposed merge/resolution for each item
- [ ] Nothing extracted that duplicates canonical without adding value

---

### Step 5: Create Delta JSON Output

**File naming:** `chapter-[##]-delta.json`  
**Location:** `editorial/extractions/deltas/`

**Structure:**
```json
{
  "source_file": "manuscript/03-chapter-1.md",
  "extraction_date": "2026-01-11",
  "extractor": "opus-4.5",
  "canonical_reference": "reference/knowledge-graph/entity-database-canonical.json",
  "canonical_version": "After Prologue merge",
  
  "updates": [
    // Array of UPDATE objects
  ],
  
  "additions": [
    // Array of ADDITION objects
  ],
  
  "contradictions": [
    // Array of CONTRADICTION objects
  ],
  
  "summary": {
    "total_updates": 0,
    "total_additions": 0,
    "total_contradictions": 0,
    "high_confidence_updates": 0,
    "additions_recommended_for_canonical": 0,
    "critical_contradictions": 0
  },
  
  "extraction_notes": {
    "chapter_themes": "[Main themes or focuses]",
    "canonical_entities_referenced": ["array"],
    "quality_concerns": ["any issues"],
    "reviewer_attention_needed": ["items needing Joshua's decision"]
  }
}
```

---

## QUALITY STANDARDS

### For UPDATES

**High Quality:**
- ✅ Clearly states what canonical currently says
- ✅ Clearly states what chapter adds
- ✅ Proposes specific merge approach
- ✅ Includes precise location

**Low Quality:**
- ❌ "Chapter mentions Scale Errors" (no actual update extracted)
- ❌ Vague proposed merge
- ❌ No location provided

---

### For ADDITIONS

**High Quality:**
- ✅ Complete entity definition per KNOWLEDGE_SCHEMA.md
- ✅ Explains why this is new (not oversight)
- ✅ Shows relationships to canonical entities
- ✅ Recommends integration approach

**Low Quality:**
- ❌ Incomplete definition
- ❌ Might actually be in canonical (didn't check thoroughly)
- ❌ No relationship mapping

---

### For CONTRADICTIONS

**High Quality:**
- ✅ Both definitions clearly stated
- ✅ Conflict precisely identified
- ✅ Severity assessed accurately
- ✅ Multiple resolution options considered
- ✅ Clear recommendation with reasoning

**Low Quality:**
- ❌ "These seem different" (vague)
- ❌ Only one resolution option
- ❌ No severity assessment
- ❌ No reasoning for recommendation

---

## SPECIAL CASES

### Case 1: Concept Appears But Doesn't Add Anything

**Situation:** Chapter mentions "Four Habitats" but adds no new information

**Action:** 
- Don't extract as UPDATE
- Note in extraction_notes that entity was referenced
- No delta needed if just mentioned in passing

---

### Case 2: Borderline Between UPDATE and CONTRADICTION

**Situation:** Chapter definition is close to canonical but slightly different

**Decision Tree:**
```
Is the difference substantive?
├─ YES → Treat as CONTRADICTION
│         (Different enough to confuse readers)
│
└─ NO → Treat as UPDATE
          (Just a different phrasing of same idea)
```

---

### Case 3: Uncertain if New or Overlooked

**Situation:** Entity seems new but might have been in Prologue implicitly

**Action:**
- Extract as ADDITION
- In "why_new" field: "Uncertain - may have been implicit in Prologue"
- Flag in extraction_notes for Joshua review
- Joshua will decide: truly new or just now explicit?

---

### Case 4: Multiple Updates to Same Entity

**Situation:** Chapter adds 3 examples to "Scale Errors"

**Action:**
- Create ONE UPDATE object
- List all contributions in "chapter_contribution" field
- Propose consolidated merge

**Example:**
```json
{
  "entity_name": "Scale Errors",
  "update_type": "multiple_examples_added",
  "chapter_contribution": "Adds three examples: (1) Family forced into market logic, (2) Market efficiency applied to safety commons, (3) Socialist planning imposed on voluntary networks",
  "proposed_merge": "Add all three to examples array in canonical"
}
```

---

## INTEGRATION WITH MERGE PROTOCOL

**After delta extraction complete:**
1. Delta JSON goes to `editorial/extractions/deltas/`
2. Joshua reviews using MERGE_PROTOCOL.md
3. Joshua approves/refines/rejects each item
4. Approved items merge into canonical database
5. Contradictions flag manuscript issues
6. Process repeats for next chapter

**Delta extraction feeds the merge protocol.**

---

## EXAMPLES: COMPLETE DELTA EXTRACTION

### Example: Chapter 1 Delta

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
      "chapter_contribution": "Adds concrete example: Trying to run family like a business destroys intimacy",
      "proposed_merge": "Add to examples array: 'Family run like business (Ch 1, para 8)'",
      "location": "Chapter 1, paragraph 8",
      "confidence": "high"
    },
    {
      "entity_name": "Four Habitats",
      "update_type": "clarification",
      "canonical_current": "Four scales where different systems operate naturally",
      "chapter_contribution": "Clarifies that we don't choose one habitat - we move through all four daily",
      "proposed_merge": "Add to definition: 'Humans navigate all four habitats continuously, not exclusively'",
      "location": "Chapter 1, paragraph 15",
      "confidence": "high"
    }
  ],
  
  "additions": [
    {
      "entity_name": "The Broken Line",
      "type": "metaphor",
      "definition": "The traditional left/right political spectrum that fails to capture the multi-dimensional reality of political systems",
      "definition_type": "book_coined",
      "builds_on": "Common 'left/right' political terminology",
      "purpose": "Explains why binary political thinking is inadequate",
      "why_new": "Chapter 1 introduces this as contrast to The Ring model",
      "first_mention": "Chapter 1, paragraph 3",
      "relates_to_canonical": ["The Ring", "System of Systems"],
      "integration_recommendation": "add_to_canonical"
    }
  ],
  
  "contradictions": [
    {
      "entity_name": "Capitalism",
      "canonical_definition": "System optimized for surplus generation through exchange at population scale",
      "chapter_definition": "Chapter 1 describes it as 'pure selfishness'",
      "conflict_type": "definition",
      "severity": "moderate",
      "location": "Chapter 1, paragraph 22",
      "analysis": "Chapter oversimplifies for rhetorical effect. Conflicts with canonical nuance.",
      "resolution_options": [
        "Keep canonical (chapter is oversimplified)",
        "Flag for manuscript revision (clarify language)"
      ],
      "recommendation": "Flag paragraph 22 for revision - avoid oversimplification"
    }
  ],
  
  "summary": {
    "total_updates": 2,
    "total_additions": 1,
    "total_contradictions": 1,
    "high_confidence_updates": 2,
    "additions_recommended_for_canonical": 1,
    "critical_contradictions": 0
  },
  
  "extraction_notes": {
    "chapter_themes": "Establishes scale errors, introduces Ring vs. Line contrast",
    "canonical_entities_referenced": ["Scale Errors", "Four Habitats", "The Ring", "Capitalism"],
    "quality_concerns": ["None"],
    "reviewer_attention_needed": ["Capitalism definition in para 22 needs revision decision"]
  }
}
```

---

## VALIDATION CHECKLIST

**Before submitting delta extraction:**

- [ ] Canonical database reviewed before extracting
- [ ] All UPDATES reference correct canonical entity
- [ ] All ADDITIONS have complete definitions per schema
- [ ] All ADDITIONS explain why they're new
- [ ] All CONTRADICTIONS cite both definitions
- [ ] All items have precise locations
- [ ] Proposed merge/resolution for every item
- [ ] Summary counts are accurate
- [ ] Extraction notes complete
- [ ] Self-validation performed

---

## COMMON MISTAKES TO AVOID

### ❌ Mistake 1: Extracting Non-Deltas

**Bad:**
```json
{
  "entity_name": "Four Habitats",
  "update_type": "mentioned",
  "chapter_contribution": "Chapter mentions Four Habitats"
}
```

**Why bad:** Mere mention is not a delta. Only extract if chapter ADDS something.

---

### ❌ Mistake 2: Missing Contradictions

**Bad:** Extracting chapter definition as ADDITION when it conflicts with canonical

**Why bad:** Creates duplicate entities instead of flagging conflict

**Correct:** Always check canonical first. If entity exists but defined differently → CONTRADICTION, not ADDITION.

---

### ❌ Mistake 3: Vague Updates

**Bad:**
```json
{
  "entity_name": "Scale Errors",
  "chapter_contribution": "Chapter talks more about this"
}
```

**Why bad:** Doesn't specify what's added. Can't merge vague updates.

**Correct:** Specify exactly what the chapter adds.

---

### ❌ Mistake 4: Not Proposing Merge

**Bad:**
```json
{
  "entity_name": "The Ring",
  "update_type": "clarification",
  "chapter_contribution": "Explains overlapping means simultaneous"
}
```

**Why bad:** No proposed merge. Joshua has to figure out integration.

**Correct:** Add `proposed_merge: "Add to definition field: 'overlapping indicates simultaneous engagement'"`

---

## EFFICIENCY TIPS

**1. Keep Canonical Open**
- Split screen: Canonical database on one side, chapter on other
- Quick reference prevents false additions

**2. Mark As You Read**
- First pass: Note potential deltas with //DELTA// comment
- Second pass: Extract systematically

**3. Group Related Updates**
- Multiple updates to same entity? Consolidate into one UPDATE object

**4. Use Templates**
- Keep example UPDATE/ADDITION/CONTRADICTION objects handy
- Copy and fill in rather than writing from scratch

---

**This delta extraction approach builds the canonical database chapter by chapter without creating competing definitions or concept drift.**
