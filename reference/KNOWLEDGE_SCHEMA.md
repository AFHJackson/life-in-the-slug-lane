# KNOWLEDGE SCHEMA
**Purpose:** Define the structure and types for the knowledge graph that ensures consistency across the book  
**Last Updated:** January 11, 2026  
**Version:** 2.0 (Added definition_type and related fields)

---

## SCHEMA OVERVIEW

This schema defines how we structure extracted entities and relationships to build a reliable knowledge graph. Consistency here enables:
- Accurate content generation
- Cross-chapter consistency
- Reliable validation
- No contradictory definitions

---

## CORE ENTITY SCHEMA

### Base Entity Structure

**All entities include these base fields:**

```json
{
  "name": "string",              // Entity name (e.g., "The Ring", "System of Systems")
  "type": "string",              // Entity type (see Entity Types below)
  "definition": "string",        // Precise definition
  "definition_type": "string",   // NEW: "technical_standard" | "book_coined" | "book_original"
  "first_mention": "string",     // Where first introduced (e.g., "Chapter 1, paragraph 3")
  "context": "string",           // Brief context of introduction
  "related_entities": ["array"]  // Names of related entities
}
```

---

## THREE-TIER DEFINITION PROTOCOL

### Type 1: Technical Standard

**For established academic/technical terms**

**Required Fields:**
```json
{
  "name": "System of Systems",
  "type": "framework",
  "definition": "A collection of task-oriented or dedicated systems that pool their resources and capabilities together to create a new, more complex system which offers more functionality and performance than simply the sum of the constituent systems",
  "definition_type": "technical_standard",
  "source": "Systems engineering",
  "book_usage": "Applied to political ideologies as constituent systems operating at different scales within a larger system of human relationships",
  "first_mention": "Prologue, paragraph 3",
  "context": "Introduced after demonstrating slug lines cannot be purely categorized",
  "related_entities": ["Slug Line", "Four Habitats", "Scale"]
}
```

**Type-Specific Fields:**
- `source` (required): Field/discipline of standard definition
- `book_usage` (required): How this book applies the technical term

---

### Type 2: Book-Coined

**For terms Joshua defines specifically for the book**

**Required Fields:**
```json
{
  "name": "Scale Errors",
  "type": "concept",
  "definition": "The mistake of applying a system designed for one scale of human relationship to a different scale where it doesn't fit",
  "definition_type": "book_coined",
  "builds_on": "Common understanding of 'scale' and 'error' but compound meaning is book-specific",
  "first_mention": "Chapter 1, title and opening",
  "context": "Central concept explaining why ideological fights happen",
  "examples": ["Forcing family to operate like market", "Applying market logic to public safety"],
  "related_entities": ["Four Habitats", "The Ring", "System of Systems"]
}
```

**Type-Specific Fields:**
- `builds_on` (optional): Common usage the term builds on

---

### Type 3: Book-Original

**For Joshua's completely original frameworks**

**Required Fields:**
```json
{
  "name": "The Ring",
  "type": "framework",
  "definition": "A circular model showing four overlapping systems arranged around a center, illustrating continuous movement through all four rather than choosing one ideology",
  "definition_type": "book_original",
  "components": ["Family (communism)", "Safety Commons (socialism)", "Markets (capitalism)", "Voluntary Networks (anarchy)"],
  "purpose": "Replaces the broken left/right spectrum with a multi-dimensional navigation tool",
  "visual_representation": "Circle/ring diagram with four quadrants",
  "first_mention": "Chapter 1, after establishing scale errors",
  "replaces": "Left/Right political spectrum",
  "related_entities": ["Four Habitats", "Scale Errors", "Left/Right Spectrum"],
  "used_throughout": true
}
```

**Type-Specific Fields:**
- `components` (optional): Parts/elements of the framework
- `purpose` (required): What problem this framework solves
- `visual_representation` (optional): Description of diagram/visual
- `replaces` (optional): What framework this supersedes

---

## ENTITY TYPES

### 1. CORE_CONCEPTS

**Types:**
- `framework`: Structured models or systems (The Ring, Four Habitats)
- `concept`: Abstract ideas or principles (Scale Errors, Emergence)
- `principle`: Rules or patterns (Obligation to Excess)
- `mechanism`: Process descriptions (Surplus → Excess → Discovery)

**Schema:**
```json
{
  "name": "string",
  "type": "framework | concept | principle | mechanism",
  "definition": "string",
  "definition_type": "technical_standard | book_coined | book_original",
  
  // Type-specific fields based on definition_type (see above)
  
  "first_mention": "string",
  "context": "string",
  "related_entities": ["array"],
  "evolution_notes": "string (optional)"
}
```

---

### 2. EXAMPLES

**Types:**
- `story_example`: Narrative examples (Slug Line, Maya's Hospital)
- `historical_reference`: Historical events/figures (Nietzsche's horse)
- `metaphor`: Comparative illustrations
- `real_world_application`: Practical applications

**Schema:**
```json
{
  "name": "string",
  "type": "story_example | historical_reference | metaphor | real_world_application",
  "description": "string",
  "illustrates": ["array"],     // Concepts this example demonstrates
  "location": "string",          // Where in manuscript
  "usage_pattern": "recurring | single_use | primary_example",
  "related_entities": ["array"],
  "narrative_arc": "string (optional)"  // If story has progression
}
```

**Example:**
```json
{
  "name": "Slug Line",
  "type": "story_example",
  "description": "Washington DC's self-organizing carpool system where strangers share rides to cross HOV lanes",
  "illustrates": ["Four Habitats", "Emergent Order", "Anarchy", "Voluntary Networks"],
  "location": "Prologue, opening story",
  "usage_pattern": "primary_example",
  "related_entities": ["Four Habitats", "Anarchy", "Emergent Order", "System of Systems"],
  "narrative_arc": "Used throughout book to demonstrate all four habitats"
}
```

---

### 3. DEFINITIONS

**For terms needing disambiguation or precise usage**

**Schema:**
```json
{
  "term": "string",
  "definition": "string",
  "definition_type": "technical_standard | book_coined | book_original",
  "usage_context": "string",
  "not_to_be_confused_with": "string (optional)",
  
  // Type-specific fields based on definition_type
  "source": "string (if technical_standard)",
  "builds_on": "string (if book_coined)",
  "purpose": "string (if book_original)"
}
```

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

## RELATIONSHIPS SCHEMA

**Relationship Types:**
- `contains`: A contains B (The Ring contains Four Habitats)
- `depends_on`: A requires understanding B (Scale Errors depends on Four Habitats)
- `contrasts_with`: A vs. B (Left/Right Spectrum vs. The Ring)
- `progresses_to`: A leads to B (Surplus → Excess)
- `illustrates`: Example demonstrates concept (Slug Line illustrates Four Habitats)
- `builds_on`: A extends B (book concept builds on technical term)

**Schema:**
```json
{
  "entity_1": "string",          // Name of first entity
  "relationship_type": "contains | depends_on | contrasts_with | progresses_to | illustrates | builds_on",
  "entity_2": "string",          // Name of second entity
  "description": "string",       // Brief explanation
  "directional": true/false,     // Is this one-way or bidirectional?
  "strength": "strong | moderate | weak (optional)"
}
```

**Examples:**
```json
{
  "entity_1": "The Ring",
  "relationship_type": "contains",
  "entity_2": "Four Habitats",
  "description": "The Ring framework consists of four habitat quadrants",
  "directional": true,
  "strength": "strong"
}
```

```json
{
  "entity_1": "Scale Errors",
  "relationship_type": "depends_on",
  "entity_2": "Four Habitats",
  "description": "Understanding scale errors requires knowing which habitats exist",
  "directional": true,
  "strength": "strong"
}
```

```json
{
  "entity_1": "Slug Line",
  "relationship_type": "illustrates",
  "entity_2": "Four Habitats",
  "description": "Slug line demonstrates all four habitats in action",
  "directional": true,
  "strength": "strong"
}
```

---

## EXTRACTION OUTPUT SCHEMA

**Complete JSON structure for each extracted file:**

```json
{
  "source_file": "string",       // Path to manuscript file
  "extraction_date": "YYYY-MM-DD",
  "extractor": "opus-4.5 | sonnet-4.5",
  "batch": "number (optional)",
  
  "entities": {
    "core_concepts": [
      {
        // Core concept schema (see above)
      }
    ],
    "examples": [
      {
        // Example schema (see above)
      }
    ],
    "definitions": [
      {
        // Definition schema (see above)
      }
    ]
  },
  
  "relationships": [
    {
      // Relationship schema (see above)
    }
  ],
  
  "extraction_notes": {
    "ambiguities": ["array"],              // Unclear definitions or usage
    "evolution_tracking": ["array"],       // Terms that may evolve later
    "cross_references": ["array"],         // References to other chapters
    "quality_concerns": ["array"],         // Any extraction issues
    "technical_terms_verified": true/false // Did we check standard definitions?
  }
}
```

---

## MASTER DATABASE SCHEMA

**Consolidated entity database structure:**

**File:** `reference/knowledge-graph/entity-database.json`

```json
{
  "metadata": {
    "last_updated": "YYYY-MM-DD",
    "total_entities": "number",
    "total_relationships": "number",
    "sources": ["array of manuscript files"],
    "schema_version": "2.0"
  },
  
  "entities": {
    "core_concepts": {
      "[entity_name]": {
        // Full entity object
        "appearances": [
          {
            "file": "string",
            "context": "string",
            "evolution": "string (if definition evolves)"
          }
        ]
      }
    },
    "examples": {
      "[example_name]": {
        // Full example object
        "appearances": ["array"]
      }
    },
    "definitions": {
      "[term]": {
        // Full definition object
      }
    }
  },
  
  "relationships": [
    // Array of all relationships
  ],
  
  "indexes": {
    "by_type": {
      "framework": ["array of names"],
      "concept": ["array of names"],
      // etc.
    },
    "by_chapter": {
      "prologue": ["array of entities"],
      "chapter-01": ["array of entities"],
      // etc.
    },
    "by_definition_type": {
      "technical_standard": ["array"],
      "book_coined": ["array"],
      "book_original": ["array"]
    }
  }
}
```

---

## VALIDATION RULES

### Required Field Validation

**All entities must have:**
- `name` (string, non-empty)
- `type` (valid entity type)
- `definition` (string, non-empty, NOT circular)
- `definition_type` (valid type: technical_standard | book_coined | book_original)

**Type-specific requirements:**

**If `definition_type: "technical_standard"`:**
- Must have `source` field
- Must have `book_usage` field
- Definition should be from recognized source, not improvised

**If `definition_type: "book_coined"`:**
- May have `builds_on` field
- Definition should be Joshua's exact wording

**If `definition_type: "book_original"`:**
- Must have `purpose` field
- May have `components` array

---

### Circular Definition Check

**Invalid (REJECT):**
```json
{
  "name": "System of Systems",
  "definition": "A system of systems is..."
}
```

**Valid:**
```json
{
  "name": "System of Systems",
  "definition": "A collection of task-oriented or dedicated systems that pool their resources..."
}
```

**Rule:** Definition text must NOT contain the entity name itself.

---

### Consistency Checks

**Across files:**
- Same entity name = same definition
- If definition evolves, track in `evolution_notes`
- Relationships must reference existing entities
- No orphaned entities (must relate to something)

---

## USAGE EXAMPLES

### Example 1: Technical Term

```json
{
  "name": "Nash Equilibrium",
  "type": "concept",
  "definition": "A solution concept in game theory where each player's strategy is optimal given the strategies of all other players, meaning no player can improve their outcome by unilaterally changing strategy",
  "definition_type": "technical_standard",
  "source": "Game theory (economics/mathematics)",
  "book_usage": "Used to explain why purely self-interested behavior in slug lines doesn't lead to chaos but to stable cooperation",
  "first_mention": "Chapter 6, when explaining emergent order",
  "context": "Demonstrates that anarchy doesn't mean disorder",
  "related_entities": ["Slug Line", "Emergent Order", "Voluntary Networks", "Game Theory"]
}
```

---

### Example 2: Book-Coined Term

```json
{
  "name": "Witching Hour",
  "type": "concept",
  "definition": "The time when HOV lane restrictions lift and the incentive for drivers to pick up extra passengers disappears, causing the slug line system to dissolve until the next day",
  "definition_type": "book_coined",
  "builds_on": "Folk term 'witching hour' meaning a time of magical transformation",
  "first_mention": "Prologue, after describing slug line operations",
  "context": "Sets up the puzzle of why the driver picked up the author after the advantage was gone",
  "examples": ["Slug Line narrative"],
  "related_entities": ["Slug Line", "Homo Economicus", "Obligation to Excess"]
}
```

---

### Example 3: Book-Original Framework

```json
{
  "name": "Four Habitats",
  "type": "framework",
  "definition": "Four distinct scales of human relationship (Family, Safety Commons, Markets, Voluntary Networks) where different organizing systems (communism, socialism, capitalism, anarchy) operate naturally and effectively",
  "definition_type": "book_original",
  "components": [
    "Family - intimate scale (communism)",
    "Safety Commons - community scale (socialism)",
    "Markets - population scale (capitalism)",
    "Voluntary Networks - flexible scale (anarchy)"
  ],
  "purpose": "Explains that political ideologies are not competing philosophies but tools optimized for different scales of human organization",
  "visual_representation": "Four quadrants within The Ring",
  "first_mention": "Chapter 1, after establishing scale errors",
  "related_entities": ["The Ring", "Scale Errors", "Communism", "Socialism", "Capitalism", "Anarchy"],
  "used_throughout": true
}
```

---

## SCHEMA EVOLUTION

**Version History:**

**v1.0 (Initial):**
- Basic entity structure
- Simple relationships

**v2.0 (Current - January 11, 2026):**
- Added `definition_type` field
- Added type-specific fields:
  - `source` and `book_usage` for technical_standard
  - `builds_on` for book_coined
  - `components` and `purpose` for book_original
- Enhanced validation rules
- Added circular definition prevention

**Future Considerations:**
- Versioning for evolving definitions
- Cross-book references (if series)
- Reader feedback integration
- Visual relationship mapping

---

## INTEGRATION WITH OTHER SYSTEMS

**This schema feeds:**

1. **Content Generation (Sonnet 4.5):**
   - Provides exact definitions to use
   - Ensures terminology consistency
   - Supplies examples for integration

2. **Validation (Opus 4.5):**
   - Reference for checking consistency
   - Definition verification
   - Relationship validation

3. **Claude.ai Project:**
   - Progress tracking
   - Continuity monitoring
   - Cross-chapter consistency

4. **Knowledge Graph Visualization:**
   - Node structure
   - Edge relationships
   - Metadata for display

---

**This schema is the authoritative structure. All entity extraction must conform to these specifications.**
