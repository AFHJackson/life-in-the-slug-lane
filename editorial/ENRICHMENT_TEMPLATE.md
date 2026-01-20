# ENRICHMENT TEMPLATE
## Enriching I→D→G Outlines for Maximum Sonnet Generation Quality

**Purpose:** This template defines the enrichment layers that Opus adds to each I→D→G outline before Sonnet generates prose. The goal is to embed enough structural precision that Sonnet can render with unified voice while Opus validates nothing is lost.

**Date Created:** Session Phase A Preparation
**Workflow:** Opus enriches → Sonnet generates → Opus validates → Human review

---

## BASELINE: What Each I→D→G Outline Already Has

Every converted outline contains:
- ✅ Target length and word count targets per phase
- ✅ Reader milestone ("By the end, reader recognizes...")
- ✅ DNA structure percentages (I/D/G split)
- ✅ Phase structure (I Opening, D Middle, G Close)
- ✅ Story entries with scene structure
- ✅ Verification invitations throughout
- ✅ Key passages and quotes
- ✅ Limits acknowledged sections
- ✅ Transitions between sections

---

## ENRICHMENT LAYERS TO ADD

### Layer 1: Cross-Chapter Thread Mapping

**Purpose:** Ensure elegant emergence and callbacks across all 13 chapters

**Format:**
```
## CROSS-CHAPTER THREADS

### Threads This Chapter Receives:
- [Thread name] from [Chapter]: [How it lands here]
- [Thread name] from [Chapter]: [How it develops here]

### Threads This Chapter Sends Forward:
- [Thread name] → [Chapter(s)]: [What must be planted here]
- [Thread name] → [Chapter(s)]: [Callback setup needed]

### Key Callbacks Required:
- Reference to [earlier element] should appear in [section]
- Echo of [phrase/concept] should land in [section]
```

**Examples to track:**
- Slug Line: Prologue → Ch 7 (full analysis) → Epilogue (callback)
- Green Acura Driver: Prologue → Ch 7 (generosity revealed)
- Four-Year-Old Performance Review: Ch 1 → Ch 3 (family context)
- Fire Department: Ch 4 → Ch 5 (underwriting) → Ch 7 (hybrid)
- Malia the Baker: Ch 9 → Ch 10 (stewardship) → Epilogue
- Matt's Week: Ch 10 → Epilogue (Ring navigator model)
- The Ring framework: Ch 1 (introduced) → Ch 8 (compass) → Ch 10 (mastery)

---

### Layer 2: Entity Mandates

**Purpose:** Ensure framework precision by mandating specific entity usage

**Format:**
```
## ENTITY MANDATES

### Must Appear (with canonical definition):
| Entity | Section | Usage Type | Canonical Definition |
|--------|---------|------------|---------------------|
| [name] | [where] | introduce/reinforce/apply | [from entity database] |

### Must NOT Appear (scope discipline):
| Entity | Why Not This Chapter |
|--------|---------------------|
| [name] | [not yet introduced / belongs to later chapter] |

### Terminology Precision:
- Use "[term A]" not "[term B]" when referring to [concept]
- "[Phrase]" is the canonical form—do not paraphrase
```

---

### Layer 3: Logical Flow Dependencies

**Purpose:** Ensure each section builds on what came before

**Format:**
```
## LOGICAL FLOW MAP

### Preconditions for This Chapter:
Reader must already understand:
- [Concept from prior chapter]
- [Framework from prior chapter]

### Internal Logic Chain:
```
[Section 1] establishes → [what it proves/shows]
     ↓
[Section 2] builds on that by → [next step]
     ↓
[Section 3] therefore can → [conclusion enabled]
```

### Verification Chain:
Each VERIFICATION INVITATION should test:
1. [What specific claim is being verified]
2. [What reader experience it should surface]
3. [What recognition it should create]
```

---

### Layer 4: Tone Markers and Voice Constraints

**Purpose:** Maintain I→D→G voice architecture with precision

**Format:**
```
## VOICE CONSTRAINTS

### Phase-Specific Tone:
| Phase | Dominant Mode | Avoid | Target Effect |
|-------|--------------|-------|---------------|
| I Opening | Wonder, curiosity | Explaining, lecturing | "Whoa, what's happening here?" |
| D Middle | Diagnostic, testing | Preaching, demanding | "Let me check this against my experience" |
| G Close | Galvanizing, agency | Hedging, retreating | "I can do this. I want to share this." |

### Forbidden Patterns:
- No "You should..." (replace with "You might notice...")
- No "The answer is..." (replace with "This suggests...")
- No "Everyone knows..." (replace with verification invitation)

### Required Patterns:
- Every major claim gets a verification invitation
- Every limit gets acknowledged
- Every transition explains the bridge
```

---

### Layer 5: Example Specifications

**Purpose:** Ensure stories render with specific sensory detail

**Format:**
```
## EXAMPLE SPECIFICATIONS

### Primary Story: [Name]

**Mandatory Scene Elements:**
- Setting: [specific details that must appear]
- Characters: [names, roles, key traits]
- Sensory anchors: [what reader should see/hear/feel]
- Emotional beat: [what reader should feel at this moment]

**Key Dialogue/Narration:**
- Must include: "[exact phrase from entity database]"
- Must convey: [specific insight]

**Do NOT:**
- [Specific thing to avoid in rendering]
- [Another thing to avoid]

### Supporting Examples:
[Same format for each]
```

---

### Layer 6: Transition Logic

**Purpose:** Ensure seamless flow between sections and chapters

**Format:**
```
## TRANSITION REQUIREMENTS

### Into This Chapter (from previous):
- Last line of [previous chapter] sets up: [what expectation]
- First paragraph here must: [fulfill that expectation]

### Between Sections:
| From | To | Bridge Required |
|------|-----|-----------------|
| Phase 1 | Section 1 | [specific bridge: "Now let's see how..."] |
| Section 1 | Section 2 | [specific bridge] |
| etc. | | |

### Out of This Chapter (to next):
- Last section must plant: [curiosity/question]
- Reader should be asking: "[specific question]"
- Next chapter opens by: [answering that question]
```

---

### Layer 7: Constraint Checklist

**Purpose:** Final verification layer before Sonnet generates

**Format:**
```
## GENERATION CONSTRAINTS

### Word Count Targets:
- Total: [X-Y words]
- Phase 1 (I): [X-Y words] ([%])
- Phase 2 (D): [X-Y words] ([%])
- Phase 3 (G): [X-Y words] ([%])

### Structural Requirements:
- [ ] Verification invitations: minimum [N] throughout D phase
- [ ] Limits acknowledged: minimum [N] sections
- [ ] Entity introductions: [list of entities that MUST appear]
- [ ] Cross-chapter callbacks: [list of required references]

### Anti-Patterns to Avoid:
- [ ] No lecturing/preaching tone
- [ ] No unsupported claims (each claim → verification)
- [ ] No false certainty (limits acknowledged where appropriate)
- [ ] No orphaned concepts (everything connects to Ring framework)
```

---

## ENRICHMENT PROCESS

For each chapter:

1. **Thread Analysis:** Map all cross-chapter connections using argument-spine.md
2. **Entity Audit:** Check entity-database-canonical.json for required entities
3. **Logic Verification:** Trace the logical dependencies within and across chapters
4. **Voice Calibration:** Mark phase boundaries with explicit tone guidance
5. **Example Enhancement:** Add sensory specifications to all stories
6. **Transition Mapping:** Explicitly connect to previous and next chapters
7. **Constraint Checklist:** Complete all verification items

---

## QUALITY STANDARD

An enriched outline is ready for Sonnet when:

- [ ] Any competent writer could generate the chapter from the outline alone
- [ ] No framework precision is left to inference
- [ ] All cross-chapter threads are explicitly mapped
- [ ] Every entity usage is specified with canonical definition
- [ ] Voice constraints are clear enough to enforce
- [ ] Validation questions can be answered yes/no from the generated text

---

## VALIDATION PROTOCOL

After Sonnet generates from enriched outline:

Opus validates by asking:
1. Does every entity appear with canonical precision?
2. Are all cross-chapter threads planted/received?
3. Does voice architecture match I→D→G percentages?
4. Are verification invitations present and well-formed?
5. Are limits acknowledged where specified?
6. Do transitions flow logically?
7. Is the reader milestone achievable from this text?

If any answer is "no," identify specific gaps and iterate.
