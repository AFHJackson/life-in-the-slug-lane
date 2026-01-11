# ENTITY EXTRACTION GUIDE
**Purpose:** Systematic process for extracting entities from manuscript files to build knowledge graph  
**Last Updated:** January 11, 2026  
**Version:** 2.0 (Added three-tier definition protocol)

---

## OVERVIEW

Entity extraction is the foundation of our knowledge graph. Quality here determines consistency throughout the entire book project.

**Goal:** Extract ALL significant concepts, examples, frameworks, and definitions to ensure:
- Consistency across chapters
- Accurate cross-references
- Reliable content generation
- No contradictions or drift

---

## THREE-TIER DEFINITION PROTOCOL

**CRITICAL:** Different entities require different definition approaches. Circular definitions (term uses itself) and improvised definitions of technical terms are **extraction failures**.

### Type 1: Technical Terms (Use Standard Definition)

**What these are:**
- Established academic/technical concepts
- Terms with recognized definitions in their field
- Standard terminology from systems theory, economics, sociology, etc.

**Examples:**
- System of systems (systems engineering)
- Emergence (complexity theory)
- Nash equilibrium (game theory)
- Public goods (economics)
- Pareto efficiency (economics)

**Extraction Protocol:**
1. **Identify:** Is this a technical term from an established field?
2. **Research:** Look up the standard academic/technical definition
3. **Extract Standard Definition:** Use the recognized definition
4. **Document Book Usage:** How does Joshua apply this term specifically?
5. **Add Fields:**
   - `definition_type: "technical_standard"`
   - `definition: "[standard technical definition]"`
   - `book_usage: "[how Joshua applies it in this book]"`
   - `source: "[field/discipline where standard definition comes from]"`

**Example (Correct):**
```json
{
  "name": "System of Systems",
  "type": "framework",
  "definition": "A collection of task-oriented or dedicated systems that pool their resources and capabilities together to create a new, more complex system which offers more functionality and performance than simply the sum of the constituent systems",
  "definition_type": "technical_standard",
  "book_usage": "Applied to political ideologies - not competing systems but constituent systems operating at different scales within a larger system of human relationships",
  "source": "Systems engineering",
  "first_mention": "Prologue, paragraph 3",
  "context": "Introduced after demonstrating slug lines cannot be categorized as purely capitalist, socialist, or anarchic",
  "related_entities": ["Slug Line", "Four Habitats", "Scale"]
}
```

**Example (INCORRECT - DO NOT DO THIS):**
```json
{
  "name": "System of Systems",
  "definition": "The recognition that we live inside a layered, overlapping system of systems where public and private, selfish and generous, structured and improvised all work together"
}
```
❌ **Problems:**
- Uses "system of systems" to define "system of systems" (circular)
- Improvised definition instead of technical definition
- Doesn't distinguish technical meaning from book application

---

### Type 2: Book-Coined Terms (Joshua's Novel Compounds)

**What these are:**
- Common words combined in novel ways
- Terms Joshua is defining specifically for this book
- May build on common usage but have specific meaning here

**Examples:**
- Scale Errors
- Witching Hour
- Obligation to Excess
- Homo Economicus (used in specific way)

**Extraction Protocol:**
1. **Identify:** Is this a term Joshua is defining/coining for the book?
2. **Extract Exact Definition:** Use Joshua's precise wording from first usage
3. **Note Common Usage:** If building on familiar terms, note the connection
4. **Add Fields:**
   - `definition_type: "book_coined"`
   - `definition: "[Joshua's exact definition from text]"`
   - `builds_on: "[common usage if applicable]"`

**Example (Correct):**
```json
{
  "name": "Scale Errors",
  "type": "concept",
  "definition": "The mistake of applying a system designed for one scale of human relationship to a different scale where it doesn't fit",
  "definition_type": "book_coined",
  "builds_on": "Common understanding of 'scale' and 'error' but compound meaning is book-specific",
  "first_mention": "Chapter 1, title and opening",
  "context": "Central concept - explains why ideological fights happen",
  "examples": ["Forcing family to operate like market", "Applying market logic to public safety"],
  "related_entities": ["Four Habitats", "The Ring", "System of Systems"]
}
```

---

### Type 3: Book-Original Frameworks (Joshua's Inventions)

**What these are:**
- Completely novel frameworks Joshua has created
- Original models, diagrams, or conceptual structures
- The book's unique intellectual contributions

**Examples:**
- The Ring
- Four Habitats
- The Slug Line (as analytic framework)

**Extraction Protocol:**
1. **Identify:** Is this Joshua's original invention?
2. **Extract Complete Description:** Get the full framework as explained
3. **Track Components:** What are the parts of this framework?
4. **Add Fields:**
   - `definition_type: "book_original"`
   - `definition: "[complete framework description]"`
   - `components: [list of framework parts]`
   - `purpose: "[what problem this framework solves]"`

**Example (Correct):**
```json
{
  "name": "The Ring",
  "type": "framework",
  "definition": "A circular model showing four overlapping systems (family, safety commons, markets, voluntary networks) arranged around a center, illustrating that we move through all four systems continuously rather than choosing one ideology over others",
  "definition_type": "book_original",
  "components": ["Family (communism)", "Safety Commons (socialism)", "Markets (capitalism)", "Voluntary Networks (anarchy)"],
  "purpose": "Replaces the broken left/right political spectrum with a multi-dimensional navigation tool",
  "first_mention": "Chapter 1, after establishing scale errors",
  "visual_representation": "Circle/ring diagram with four quadrants",
  "related_entities": ["Four Habitats", "Scale Errors", "Left/Right Spectrum"],
  "used_throughout": true
}
```

---

## DECISION TREE: Which Definition Type?

**When extracting any entity, ask:**

```
Is this a technical term from an established field?
│
├─ YES → Type 1: Technical Standard
│         • Research standard definition
│         • Extract technical meaning
│         • Document book_usage
│         • Add source field
│
└─ NO → Is Joshua defining this specifically for the book?
         │
         ├─ YES, building on common words → Type 2: Book-Coined
         │         • Extract Joshua's exact definition
         │         • Note what common usage it builds on
         │
         └─ YES, completely original → Type 3: Book-Original
                   • Extract complete framework
                   • List components
                   • Note purpose
```

---

## ENTITY CATEGORIES

### 1. CORE CONCEPTS

**What to extract:**
- Frameworks (The Ring, Four Habitats, Scale Errors)
- Systems (Communism, Socialism, Capitalism, Anarchy as systems)
- Mechanisms (Surplus → Excess → Discovery/Generosity)
- Principles (stated rules or patterns)
- Theoretical concepts (Homo Economicus, etc.)

**For each, determine:**
- Which definition type? (technical_standard, book_coined, book_original)
- What's the precise definition?
- Where first mentioned?
- What does it relate to?

---

### 2. EXAMPLES & STORIES

**What to extract:**
- Named examples (Slug Line, Nail-Maker, Maya's Hospital)
- Historical references (Nietzsche's horse, etc.)
- Real-world applications
- Metaphors and analogies

**Schema:**
```json
{
  "name": "Slug Line",
  "type": "story_example",
  "description": "Washington DC's self-organizing carpool system where strangers share rides to cross HOV lanes",
  "illustrates": ["Four Habitats", "Emergent Order", "Anarchy", "Voluntary Networks"],
  "location": "Prologue, opening story",
  "usage_pattern": "Primary recurring example throughout book",
  "related_entities": ["Four Habitats", "Anarchy", "Emergent Order"]
}
```

---

### 3. DEFINITIONS & TERMS

**What to extract:**
- Technical vocabulary with specific meanings
- Terms needing disambiguation
- Phrases with precise usage

**Example:**
```json
{
  "term": "Habitat",
  "definition": "A scale of human relationship where a particular system operates naturally",
  "definition_type": "book_coined",
  "builds_on": "Biological sense of 'habitat' as natural environment",
  "usage_context": "Always used with 'Four Habitats' framework",
  "not_to_be_confused_with": "Literal biological habitat"
}
```

---

### 4. RELATIONSHIPS

**Types to capture:**

**Containment:**
- "The Ring contains Four Habitats"
- "Four Habitats consists of Family, Safety Commons, Markets, Voluntary Networks"

**Dependency:**
- "Understanding Scale Errors depends on understanding Four Habitats"
- "Surplus mechanism requires Markets habitat"

**Contrast:**
- "Left/Right Spectrum vs. The Ring"
- "Homo Economicus vs. actual human behavior in Slug Line"

**Progression:**
- "Surplus → Excess → Discovery/Generosity"
- "Scale → System → Habitat"

**Illustration:**
- "Slug Line illustrates Four Habitats"
- "Nail-Maker illustrates Surplus mechanism"

---

## EXTRACTION QUALITY STANDARDS

### Before Finalizing Any Extraction:

**Self-Check Questions:**

1. **Circular Definitions:**
   - ❌ Does any definition use the term itself?
   - ❌ "System of Systems is a system of systems..."
   - ✅ Definitions should use OTHER terms to explain the concept

2. **Technical Terms:**
   - ❌ Did I improvise a definition for a technical term?
   - ✅ Did I research and use the standard definition?
   - ✅ Did I document how the book applies it?

3. **Completeness:**
   - ✅ Did I extract ALL significant concepts from this file?
   - ✅ Did I capture first mentions?
   - ✅ Did I note relationships?

4. **Consistency:**
   - ✅ Does this match extraction patterns from previous files?
   - ✅ Are entity types used consistently?

5. **Book-Coined Terms:**
   - ✅ Did I use Joshua's exact wording for book-specific definitions?
   - ✅ Did I note if it builds on common usage?

---

## UPDATED JSON SCHEMA

**Full entity template:**

```json
{
  "source_file": "manuscript/02-prologue.md",
  "extraction_date": "2026-01-11",
  "extractor": "opus-4.5",
  "entities": {
    "core_concepts": [
      {
        "name": "[Entity name]",
        "type": "framework | concept | principle | mechanism",
        "definition": "[Precise definition - see three-tier protocol]",
        "definition_type": "technical_standard | book_coined | book_original",
        
        // If technical_standard:
        "book_usage": "[How book applies this technical term]",
        "source": "[Academic field or discipline]",
        
        // If book_coined:
        "builds_on": "[Common usage if applicable]",
        
        // If book_original:
        "components": ["[Part 1]", "[Part 2]"],
        "purpose": "[What problem this solves]",
        
        // All types:
        "first_mention": "[Location in text]",
        "context": "[Brief context of introduction]",
        "related_entities": ["[Entity 1]", "[Entity 2]"],
        "evolution_notes": "[If definition evolves across chapters]"
      }
    ],
    "examples": [
      {
        "name": "[Example name]",
        "type": "story_example | historical_reference | metaphor | real_world_application",
        "description": "[Brief summary]",
        "illustrates": ["[Concept 1]", "[Concept 2]"],
        "location": "[Where in file]",
        "usage_pattern": "[recurring | single_use | primary_example]",
        "related_entities": ["[Entity 1]", "[Entity 2]"]
      }
    ],
    "definitions": [
      {
        "term": "[Term]",
        "definition": "[Definition]",
        "definition_type": "technical_standard | book_coined | book_original",
        "usage_context": "[When/how used]",
        "not_to_be_confused_with": "[Common misunderstandings if applicable]"
      }
    ]
  },
  "relationships": [
    {
      "entity_1": "[Entity A]",
      "relationship_type": "contains | depends_on | contrasts_with | progresses_to | illustrates | builds_on",
      "entity_2": "[Entity B]",
      "description": "[Brief explanation of relationship]"
    }
  ],
  "extraction_notes": {
    "ambiguities": ["[Any unclear definitions or usage]"],
    "evolution_tracking": ["[Terms that may evolve in later chapters]"],
    "cross_references": ["[References to other chapters]"]
  }
}
```

---

## BATCH PROCESSING WORKFLOW

### Recommended Batch Sizes: 3-4 files per batch

**Why:**
- Maintains quality and focus
- Allows for learning and refinement
- Prevents overwhelming the system

### For Each Batch:

**Step 1: Read Extraction Guide** (this document)
- Review three-tier definition protocol
- Refresh on quality standards

**Step 2: Read Knowledge Schema**
- Understand current entity types
- Check for consistency with previous batches

**Step 3: Process Files Systematically**
- One file at a time
- Extract all categories
- Apply definition protocols
- Check quality before moving to next file

**Step 4: Create JSON Outputs**
- One JSON file per manuscript file
- Follow naming convention: `[file-name]-entities.json`
- Save to: `editorial/extractions/`

**Step 5: Self-Validation**
- Review all core_concepts for circular definitions
- Verify technical terms have proper definitions
- Check for completeness
- Note any concerns in extraction_notes

**Step 6: Summary Report**
- Total entities extracted
- Key frameworks identified
- Any ambiguities or concerns
- Readiness for integration

---

## COMMON EXTRACTION ERRORS TO AVOID

### ❌ ERROR 1: Circular Definition
**Bad:**
```json
{
  "name": "System of Systems",
  "definition": "A system of systems where multiple systems work together"
}
```

**Good:**
```json
{
  "name": "System of Systems",
  "definition": "A collection of task-oriented or dedicated systems that pool their resources and capabilities together to create a new, more complex system",
  "definition_type": "technical_standard"
}
```

---

### ❌ ERROR 2: Improvised Technical Definition
**Bad:**
```json
{
  "name": "Emergence",
  "definition": "When stuff happens that you didn't plan"
}
```

**Good:**
```json
{
  "name": "Emergence",
  "definition": "The process by which complex patterns, structures, or behaviors arise from relatively simple interactions among components, where the whole exhibits properties not present in the individual parts",
  "definition_type": "technical_standard",
  "source": "Complexity theory",
  "book_usage": "Applied to slug lines and voluntary networks showing order without central planning"
}
```

---

### ❌ ERROR 3: Missing Book Application for Technical Term
**Bad:**
```json
{
  "name": "Public Goods",
  "definition": "[standard economics definition]",
  "definition_type": "technical_standard"
}
```

**Good:**
```json
{
  "name": "Public Goods",
  "definition": "Goods that are non-excludable and non-rivalrous, meaning one person's use doesn't diminish another's ability to use them",
  "definition_type": "technical_standard",
  "source": "Economics",
  "book_usage": "Used to explain the Safety Commons habitat where socialist systems operate naturally",
  "related_entities": ["Safety Commons", "Socialism"]
}
```

---

### ❌ ERROR 4: Incomplete Framework Extraction
**Bad:**
```json
{
  "name": "The Ring",
  "definition": "A circle showing the four systems"
}
```

**Good:**
```json
{
  "name": "The Ring",
  "type": "framework",
  "definition": "A circular model showing four overlapping systems arranged around a center, illustrating continuous movement through all four rather than choosing one ideology",
  "definition_type": "book_original",
  "components": ["Family", "Safety Commons", "Markets", "Voluntary Networks"],
  "purpose": "Replaces broken left/right spectrum with multi-dimensional navigation tool",
  "visual_representation": "Circle/ring with four quadrants",
  "replaces": "Left/Right political spectrum"
}
```

---

## SPECIAL CASES

### Case 1: Term Evolves Across Chapters

**Approach:**
- Extract first definition
- Note in `evolution_notes` field
- Track changes in later batches
- Flag for consistency review

**Example:**
```json
{
  "name": "Obligation to Excess",
  "definition": "[Initial definition from first mention]",
  "first_mention": "Chapter 5",
  "evolution_notes": "Concept introduced in Ch 5, fully explained in Ch 9"
}
```

---

### Case 2: Multiple Competing Definitions in Text

**Approach:**
- Extract dominant/primary definition
- Note alternatives in `extraction_notes`
- Flag for Joshua review
- May indicate need for clarification

---

### Case 3: Implicit vs. Explicit Definitions

**Approach:**
- Prefer explicit definitions (where Joshua defines directly)
- If only implicit, extract based on usage patterns
- Note in `context` field: "Definition inferred from usage"
- Flag for potential explicit definition in revision

---

## INTEGRATION WITH KNOWLEDGE GRAPH

### After Extraction:

**Extracted entities feed into:**
- `reference/knowledge-graph/entity-database.json` (master database)
- `reference/knowledge-graph/relationship-map.json` (how entities connect)
- `reference/knowledge-graph/framework-library.md` (frameworks explained)
- `reference/knowledge-graph/example-catalog.md` (examples indexed)

**Quality at extraction = Quality throughout project**

---

## VALIDATION CHECKLIST

**Before marking batch complete:**

- [ ] All files in batch processed
- [ ] All core concepts have proper definition_type
- [ ] No circular definitions (term uses itself)
- [ ] All technical terms have standard definitions + book_usage
- [ ] All book-coined terms use Joshua's exact wording
- [ ] All book-original frameworks have components listed
- [ ] Relationships documented
- [ ] JSON files properly formatted
- [ ] Extraction notes include any concerns
- [ ] Summary report completed

---

**This guide is the authoritative process. Follow it precisely for consistent, high-quality entity extraction.**
