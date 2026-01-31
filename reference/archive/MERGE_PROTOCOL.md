# MERGE PROTOCOL
**Purpose:** Review delta extractions and integrate approved changes into canonical database  
**Version:** 1.0  
**Date:** January 11, 2026

---

## OVERVIEW

**After each chapter delta extraction, you (Joshua) review and merge changes into the canonical entity database.**

**This protocol provides:**
- Decision framework for each delta type
- Merge procedures
- Quality gates
- Conflict resolution strategies

---

## THREE-STAGE MERGE PROCESS

```
Stage 1: Review UPDATES → Approve/Refine/Reject
    ↓
Stage 2: Review ADDITIONS → Add/Merge/Trim
    ↓
Stage 3: Review CONTRADICTIONS → Resolve conflicts
    ↓
Update canonical database
    ↓
Log changes in evolution-log.md
```

---

## STAGE 1: REVIEWING UPDATES

**Updates are refinements to existing canonical entities.**

### Decision Framework

**For each UPDATE, ask:**

**Question 1: Does this actually add value?**
- ✅ YES → Continue to Question 2
- ❌ NO → Reject (no change to canonical)

**Question 2: Is the addition accurate to the book's argument?**
- ✅ YES → Continue to Question 3
- ❌ NO → Reject or flag for manuscript revision

**Question 3: How should it integrate?**
- **Approve as-is** → Merge exactly as proposed
- **Approve with refinement** → Adjust wording, then merge
- **Reject** → Keep canonical unchanged

---

### Update Types & Merge Actions

#### UPDATE TYPE: Example Added

**Review:**
- Does example truly illustrate the concept?
- Is example clear and memorable?
- Does it duplicate existing examples?

**Merge Action:**
```json
// BEFORE (Canonical)
{
  "name": "Scale Errors",
  "definition": "...",
  "examples": [
    "Slug line demonstrates all four habitats (Prologue)"
  ]
}

// AFTER (Merged)
{
  "name": "Scale Errors",
  "definition": "...",
  "examples": [
    "Slug line demonstrates all four habitats (Prologue)",
    "Family forced to operate like business (Ch 1)" // ADDED
  ],
  "evolution": [
    {
      "chapter": "Chapter 1",
      "change": "Added example: family/business scale error",
      "date": "2026-01-11"
    }
  ]
}
```

---

#### UPDATE TYPE: Clarification

**Review:**
- Does clarification genuinely improve understanding?
- Does it contradict anything in canonical?
- Is wording clear?

**Merge Action:**
```json
// BEFORE (Canonical)
{
  "name": "Four Habitats",
  "definition": "Four distinct scales of human relationship where different systems operate naturally"
}

// AFTER (Merged)
{
  "name": "Four Habitats",
  "definition": "Four distinct scales of human relationship where different systems operate naturally. Humans navigate all four continuously, not exclusively.",
  "evolution": [
    {
      "chapter": "Chapter 1",
      "change": "Clarified continuous simultaneous navigation",
      "date": "2026-01-11"
    }
  ]
}
```

---

#### UPDATE TYPE: Refinement

**Review:**
- Does refinement improve precision?
- Does it change meaning or just enhance it?
- Is new wording better than canonical?

**Merge Action Options:**

**Option A: Replace definition**
```json
// If refined version is clearly better
{
  "name": "...",
  "definition": "[NEW refined definition]",
  "evolution": [
    {
      "chapter": "Chapter X",
      "change": "Definition refined for clarity",
      "previous_definition": "[OLD definition]",
      "date": "2026-01-11"
    }
  ]
}
```

**Option B: Add refinement note**
```json
// If refinement is additive, not replacement
{
  "name": "...",
  "definition": "[Original definition]",
  "refinements": [
    "Chapter X adds: [specific refinement]"
  ]
}
```

---

#### UPDATE TYPE: New Application

**Review:**
- Is this truly a new application or just restating?
- Does it expand the framework's reach?

**Merge Action:**
```json
{
  "name": "...",
  "applications": [
    "Original application (Prologue)",
    "New application domain (Chapter X)" // ADDED
  ]
}
```

---

### Update Review Workflow

**For each UPDATE in chapter delta:**

1. **Open canonical database**
2. **Find the entity being updated**
3. **Read current canonical definition**
4. **Read proposed update**
5. **Decide: Approve / Refine / Reject**
6. **If approved: Apply merge**
7. **Add evolution log entry**
8. **Mark UPDATE as processed**

**Track decisions:**
- ✅ Approved (merged)
- ✏️ Approved with changes (refined and merged)
- ❌ Rejected (canonical unchanged)

---

## STAGE 2: REVIEWING ADDITIONS

**Additions are new entities not in canonical database.**

### Decision Framework

**For each ADDITION, ask:**

**Question 1: Is this genuinely new or was it overlooked in Prologue?**
- **Genuinely new** → Continue to Question 2
- **Overlooked** → Add to canonical (note in evolution log)
- **Uncertain** → Flag for deeper review

**Question 2: Does this serve the book?**
- ✅ **Core concept** → Add to canonical
- 🔀 **Similar to existing** → Consider merging
- ✂️ **Tangential branch** → Trim (don't add)

**Question 3: How should it integrate?**
- **Add as new entity** → Full addition to canonical
- **Merge with existing** → Consolidate similar concepts
- **Trim** → Concept doesn't serve book (cut from manuscript)

---

### Addition Types & Actions

#### ACTION: Add as New Entity

**When to use:**
- Concept is distinct and necessary
- No canonical entity covers this
- Serves the book's argument

**Merge Action:**
```json
// Add complete entity to canonical database
{
  "name": "Obligation to Excess",
  "type": "principle",
  "definition": "...",
  "definition_type": "book_original",
  "purpose": "...",
  "first_mention": "Chapter 5",
  "added_in_chapter": 5,
  "date_added": "2026-01-11"
}
```

**Log in evolution-log.md:**
```markdown
### Chapter 5 Additions
- **Obligation to Excess** - New principle introduced to explain behavior beyond pure self-interest
```

---

#### ACTION: Merge with Existing

**When to use:**
- New concept is similar to canonical entity
- Consolidation would strengthen both
- Prevents concept branching

**Example:**
```
ADDITION: "Mutual Aid" (Chapter 6)
CANONICAL: "Generosity" (Prologue)

DECISION: Merge into single concept "Generosity/Mutual Aid"
```

**Merge Action:**
```json
{
  "name": "Generosity", // Keep canonical name as primary
  "aliases": ["Mutual Aid"], // Add new name as alias
  "definition": "[Merged definition incorporating both]",
  "evolution": [
    {
      "chapter": "Chapter 6",
      "change": "Incorporated mutual aid concept, added as alias",
      "reasoning": "Prevents concept branching - same underlying idea",
      "date": "2026-01-11"
    }
  ]
}
```

---

#### ACTION: Trim

**When to use:**
- Concept is tangential to main argument
- Creates unnecessary branching
- Distracts from core frameworks

**Process:**
1. Don't add to canonical
2. Note in trimmed-concepts-log.md
3. Consider manuscript revision (cut from chapter)

**Log in trimmed-concepts-log.md:**
```markdown
### Chapter 3 - Trimmed Concepts
- **"Communal Responsibility"** - Too similar to existing "Obligation to Excess" - cut to avoid confusion
- **Reasoning:** Same idea with different words, doesn't add value
- **Manuscript action:** Revise Chapter 3, paragraph 18 to use "Obligation to Excess" terminology
```

---

### Addition Review Workflow

**For each ADDITION in chapter delta:**

1. **Check: Is this truly new?**
   - Search canonical database thoroughly
   - Check aliases and similar concepts

2. **Decide action: Add / Merge / Trim**

3. **If Add:**
   - Add complete entity to canonical
   - Log in evolution-log.md

4. **If Merge:**
   - Update canonical entity with merged definition
   - Add alias if appropriate
   - Log merge reasoning

5. **If Trim:**
   - Don't add to canonical
   - Log in trimmed-concepts-log.md
   - Flag manuscript paragraph for revision

6. **Mark ADDITION as processed**

---

## STAGE 3: REVIEWING CONTRADICTIONS

**Contradictions are conflicts between chapter and canonical definitions.**

### Decision Framework

**For each CONTRADICTION, ask:**

**Question 1: Which is correct?**
- **Canonical is correct** → Keep canonical, flag chapter for revision
- **Chapter is correct** → Update canonical (evolution log the change)
- **Both have merit** → Synthesize/merge
- **Genuine conflict** → Flag for manuscript rewrite

**Question 2: How severe is the confusion this could cause?**
- **Critical** → Must resolve before proceeding
- **Moderate** → Should resolve but can continue
- **Minor** → Note but may not need action

---

### Contradiction Severity Levels

#### CRITICAL Contradictions

**Characteristics:**
- Core framework definitions conflict
- Would confuse readers fundamentally
- Undermines book's argument

**Action:**
- MUST resolve before finalizing chapter
- Usually requires manuscript revision
- May require rethinking framework

**Example:**
```
CANONICAL: "We move through all four habitats continuously"
CHAPTER: "Choose which habitat to operate in"

SEVERITY: Critical
ACTION: Manuscript revision required - Chapter contradicts core framework
```

---

#### MODERATE Contradictions

**Characteristics:**
- Definitions differ but not fundamentally
- Could confuse but not destroy understanding
- Might be reconcilable

**Action:**
- Should resolve but book can proceed
- Evaluate which version is clearer
- Consider synthesis

**Example:**
```
CANONICAL: "Capitalism optimized for surplus generation"
CHAPTER: "Capitalism is pure selfishness"

SEVERITY: Moderate
ACTION: Chapter oversimplifies - flag for refinement but not critical error
```

---

#### MINOR Contradictions

**Characteristics:**
- Slight wording differences
- Same core meaning, different expression
- Unlikely to confuse readers

**Action:**
- Note but may not require change
- Choose clearer wording for canonical
- Low priority for manuscript revision

**Example:**
```
CANONICAL: "Scale errors occur when..."
CHAPTER: "Scale mistakes happen when..."

SEVERITY: Minor
ACTION: Keep canonical "errors" terminology, note variance
```

---

### Contradiction Resolution Strategies

#### STRATEGY 1: Canonical Wins

**When to use:**
- Canonical definition is clearer
- Chapter is imprecise or oversimplified
- Canonical has been refined through multiple chapters

**Action:**
```markdown
DECISION: Keep canonical definition
MANUSCRIPT ACTION: Flag Chapter X, paragraph Y for revision
REASONING: [Why canonical is better]
```

**Log in contradiction-log.md:**
```markdown
### Chapter 5 - Contradiction #1
- **Entity:** Capitalism
- **Canonical:** "System optimized for surplus generation"
- **Chapter:** "Pure selfishness"
- **Resolution:** Kept canonical, flagged para 22 for revision
- **Reasoning:** Chapter oversimplifies for rhetoric, loses nuance
- **Severity:** Moderate
```

---

#### STRATEGY 2: Chapter Wins

**When to use:**
- Chapter definition is clearer/better
- Chapter represents evolution of thinking
- Canonical was imprecise

**Action:**
```json
// Update canonical with chapter definition
{
  "name": "...",
  "definition": "[CHAPTER definition - now canonical]",
  "evolution": [
    {
      "chapter": "Chapter X",
      "change": "Definition updated based on chapter refinement",
      "previous_definition": "[OLD canonical definition]",
      "reasoning": "Chapter version is clearer and more precise",
      "date": "2026-01-11"
    }
  ]
}
```

---

#### STRATEGY 3: Synthesize/Merge

**When to use:**
- Both definitions have merit
- Synthesis creates better definition
- Captures nuance from both

**Action:**
```json
{
  "name": "...",
  "definition": "[NEW synthesized definition incorporating both]",
  "evolution": [
    {
      "chapter": "Chapter X",
      "change": "Definition synthesized from canonical + chapter versions",
      "canonical_contribution": "[what canonical provided]",
      "chapter_contribution": "[what chapter provided]",
      "synthesis_reasoning": "[why merged version is better]",
      "date": "2026-01-11"
    }
  ]
}
```

---

#### STRATEGY 4: Flag for Manuscript Rewrite

**When to use:**
- Genuine logical contradiction (both can't be true)
- Indicates conceptual confusion in manuscript
- Framework needs rethinking

**Action:**
```markdown
CRITICAL CONTRADICTION - MANUSCRIPT REVISION REQUIRED

Entity: [Name]
Location: Chapter X, paragraphs Y-Z
Issue: [Description of fundamental conflict]
Impact: Undermines [framework/argument]
Resolution needed: [What needs to be rewritten]
```

**This goes in critical-issues-log.md for immediate attention.**

---

### Contradiction Review Workflow

**For each CONTRADICTION in chapter delta:**

1. **Read both definitions carefully**
2. **Assess severity: Critical / Moderate / Minor**
3. **If Critical: Stop and resolve before proceeding**
4. **Choose resolution strategy:**
   - Canonical wins
   - Chapter wins
   - Synthesize
   - Flag for rewrite
5. **Apply resolution**
6. **Log in contradiction-log.md**
7. **If manuscript revision needed: Flag in critical-issues-log.md**
8. **Mark CONTRADICTION as processed**

---

## CANONICAL DATABASE UPDATE PROCEDURE

**After reviewing all deltas (Updates, Additions, Contradictions):**

### Step 1: Backup Current Canonical

```bash
# In VS Code terminal
cp reference/knowledge-graph/entity-database-canonical.json \
   reference/knowledge-graph/entity-database-canonical-backup-[date].json
```

**Why:** Safety net in case you need to revert

---

### Step 2: Apply All Approved Changes

**Open canonical database JSON**

**For UPDATES:**
- Modify existing entities
- Add to examples arrays
- Append to evolution logs

**For ADDITIONS:**
- Add new entity objects
- Ensure proper schema
- Add relationships

**For CONTRADICTIONS:**
- Apply resolution (canonical/chapter/synthesis)
- Update definitions as decided
- Log changes

---

### Step 3: Validate Schema

**Check:**
- [ ] JSON is valid (no syntax errors)
- [ ] All entities have required fields
- [ ] No duplicate entity names
- [ ] Relationships reference existing entities
- [ ] Evolution logs are complete

---

### Step 4: Commit Changes

```bash
git add reference/knowledge-graph/entity-database-canonical.json
git commit -m "Merge Chapter X deltas: [summary]"
git push
```

**Commit message should include:**
- Chapter number
- Number of updates/additions/contradictions
- Any critical decisions

**Example:**
```
Merge Chapter 1 deltas: 2 updates, 1 addition, 1 contradiction resolved
- Added "The Broken Line" concept
- Clarified Four Habitats continuous navigation
- Resolved Capitalism definition conflict (kept canonical)
```

---

## LOGGING & DOCUMENTATION

### evolution-log.md

**Purpose:** Track how canonical database grows chapter by chapter

**Format:**
```markdown
# CANONICAL DATABASE EVOLUTION LOG

## Chapter 1 Merge (2026-01-11)

### Updates Applied (2)
- **Scale Errors:** Added example "Family as business" (para 8)
- **Four Habitats:** Clarified continuous navigation (para 15)

### Additions (1)
- **The Broken Line:** New metaphor for inadequate left/right spectrum

### Contradictions Resolved (1)
- **Capitalism:** Kept canonical definition, flagged Chapter 1 para 22 for revision (oversimplification)

### Canonical Status
- Total entities: 15
- Chapters integrated: Prologue, Chapter 1
- Pending contradictions: 0
```

---

### contradiction-log.md

**Purpose:** Track all contradictions and resolutions

**Format:**
```markdown
# CONTRADICTION RESOLUTION LOG

## Chapter 1 Contradictions

### Contradiction #1: Capitalism Definition
- **Canonical:** "System optimized for surplus generation"
- **Chapter:** "Pure selfishness" (para 22)
- **Severity:** Moderate
- **Resolution:** Kept canonical, flagged para 22 for revision
- **Reasoning:** Chapter oversimplifies for rhetoric, loses nuance
- **Date:** 2026-01-11
```

---

### trimmed-concepts-log.md

**Purpose:** Track concepts that were cut (not added to canonical)

**Format:**
```markdown
# TRIMMED CONCEPTS LOG

## Chapter 3 Trims

### "Communal Responsibility"
- **Why trimmed:** Too similar to existing "Obligation to Excess"
- **Decision:** Merge concepts, use "Obligation to Excess" terminology
- **Manuscript action:** Revise Chapter 3, para 18
- **Date:** 2026-01-11
```

---

### critical-issues-log.md

**Purpose:** Track critical contradictions requiring manuscript revision

**Format:**
```markdown
# CRITICAL ISSUES LOG

## Chapter 5 - CRITICAL Contradiction

### Issue: Four Habitats Choice vs. Navigation
- **Location:** Chapter 5, paragraphs 12-18
- **Problem:** Chapter suggests "choosing which habitat to operate in" which contradicts core framework that we're always in all four simultaneously
- **Impact:** Could fundamentally confuse readers about book's central thesis
- **Resolution Required:** Rewrite paragraphs 12-18 to align with canonical framework
- **Status:** ⚠️ BLOCKING - Must resolve before finalizing Chapter 5
- **Date Identified:** 2026-01-11
```

---

## MERGE SESSION WORKFLOW

**Complete workflow for each chapter delta:**

### Pre-Merge

1. **Backup canonical database**
2. **Open delta JSON file**
3. **Open canonical database JSON**
4. **Have logs ready** (evolution, contradiction, trimmed)

---

### During Merge

**UPDATES:**
- [ ] Review each update
- [ ] Decide: Approve / Refine / Reject
- [ ] Apply approved updates to canonical
- [ ] Log changes in evolution-log.md

**ADDITIONS:**
- [ ] Review each addition
- [ ] Decide: Add / Merge / Trim
- [ ] Apply to canonical or log trim
- [ ] Update evolution-log.md or trimmed-concepts-log.md

**CONTRADICTIONS:**
- [ ] Review each contradiction
- [ ] Assess severity
- [ ] Choose resolution strategy
- [ ] Apply resolution to canonical
- [ ] Log in contradiction-log.md
- [ ] If critical: Log in critical-issues-log.md

---

### Post-Merge

1. **Validate canonical JSON schema**
2. **Count final entities**
3. **Review evolution log for completeness**
4. **Commit changes to Git**
5. **Update PROGRESS_TRACKER.md**
6. **Mark chapter delta as merged**
7. **Proceed to next chapter delta**

---

## QUALITY GATES

**Before considering merge complete:**

- [ ] All updates reviewed and decided
- [ ] All additions reviewed and decided
- [ ] All contradictions resolved
- [ ] Canonical database validates (no JSON errors)
- [ ] Evolution log updated
- [ ] Any contradictions logged
- [ ] Any trims logged
- [ ] Critical issues logged (if any)
- [ ] Changes committed to Git
- [ ] PROGRESS_TRACKER.md updated

---

## DECISION RECORD TEMPLATE

**For your own tracking, keep notes:**

```markdown
# Chapter X Merge Session
Date: 2026-01-11
Duration: 30 minutes

## Updates Processed: 3
- ✅ Approved: 2
- ✏️ Refined: 1
- ❌ Rejected: 0

## Additions Processed: 2
- ➕ Added: 1
- 🔀 Merged: 1
- ✂️ Trimmed: 0

## Contradictions Processed: 1
- Canonical wins: 1
- Chapter wins: 0
- Synthesized: 0
- Flagged for rewrite: 0

## Critical Issues: 0

## Notes:
[Any observations, patterns, concerns]

## Next Chapter Ready: ✅
```

---

**This merge protocol ensures systematic, documented integration of each chapter's contributions into the growing canonical database.**
