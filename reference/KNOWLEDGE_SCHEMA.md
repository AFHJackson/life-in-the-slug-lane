# KNOWLEDGE SCHEMA
**Purpose:** Database structure for manuscript knowledge graph  
**Last Updated:** January 10, 2026

---

## OVERVIEW

### What is the Knowledge Schema?

**The technical specification for how we store and query all manuscript entities.**

This schema defines:
- JSON structure for entity database
- Relationship types and how they connect
- Query patterns for agent access
- Validation rules
- Update protocols
- Versioning approach

**File Location:** `reference/knowledge-graph/entity-database.json`

**Primary Users:**
- **Opus 4.5:** Extracts entities, validates structure
- **Sonnet 4.5:** Queries for continuity, generates consistent content
- **Claude.ai Project:** Orchestrates updates, maintains master database

---

## DATABASE STRUCTURE

### Top-Level Schema
```json
{
  "metadata": {
    "schema_version": "1.0.0",
    "last_updated": "YYYY-MM-DD",
    "total_entities": 0,
    "manuscript_version": "draft|final",
    "extraction_complete": false
  },
  "entities": [],
  "relationships": [],
  "indexes": {
    "by_type": {},
    "by_chapter": {},
    "by_name": {}
  },
  "validation_log": []
}
```

---

### Metadata Block

**Purpose:** Track database state and versioning
```json
{
  "metadata": {
    "schema_version": "1.0.0",
    "last_updated": "2026-01-10",
    "total_entities": 127,
    "manuscript_version": "draft",
    "extraction_complete": false,
    "chapters_extracted": [
      "prologue",
      "1",
      "2",
      "3",
      "4",
      "5",
      "6",
      "7",
      "8"
    ],
    "chapters_pending": [
      "9",
      "10",
      "epilogue",
      "appendix"
    ],
    "last_extraction": {
      "chapter": "8",
      "date": "2026-01-10",
      "entity_count": 15,
      "extractor": "opus-4.5"
    }
  }
}
```

**Fields:**
- `schema_version`: Semantic version of this schema (for future upgrades)
- `last_updated`: ISO date of last modification
- `total_entities`: Count of entities in database
- `manuscript_version`: Current state (draft/final/published)
- `extraction_complete`: Boolean - have all chapters been extracted?
- `chapters_extracted`: List of completed chapters
- `chapters_pending`: List awaiting extraction
- `last_extraction`: Details of most recent extraction operation

---

### Entities Array

**Purpose:** Store all extracted entities

**Structure:** Array of entity objects, each following entity type schema
```json
{
  "entities": [
    {
      "entity_id": "unique-id",
      "entity_type": "type",
      "name": "Name",
      // ... type-specific fields
    },
    // ... more entities
  ]
}
```

**Entity Types:** 7 types, each with specific schema (detailed below)

1. Character
2. Framework
3. Example
4. Metaphor
5. Location
6. Claim
7. Promise

---

## ENTITY TYPE SCHEMAS

### 1. Character Schema
```json
{
  "entity_id": "char-{slug}",
  "entity_type": "character",
  "name": "Character Name",
  "first_appearance": {
    "chapter": "prologue|1-10|epilogue|appendix",
    "section": "Section Name",
    "paragraph": 0,
    "context": "Brief description"
  },
  "definition": "Who this character is",
  "attributes": {
    "occupation": "Job/role",
    "age_range": "Approximate age",
    "key_traits": ["trait1", "trait2"],
    "narrative_role": "Purpose in narrative"
  },
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "What happens here",
      "reference_type": "full|brief|mention",
      "speaking_role": true,
      "primary_focus": true
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "illustrates|knows|works-with|opposes",
      "description": "Nature of relationship"
    }
  ],
  "consistency_checks": [
    {
      "attribute": "occupation",
      "values_found": ["value1", "value2"],
      "chapters": ["1", "5"],
      "status": "consistent|inconsistent",
      "notes": "Details"
    }
  ],
  "promises": [],
  "tags": ["reader-proxy", "recurring", "example-character"],
  "last_updated": "YYYY-MM-DD"
}
```

**Field Definitions:**

- `entity_id`: Format `char-{slug}` where slug is lowercase-hyphenated name
- `entity_type`: Always "character"
- `name`: Exact as appears in manuscript
- `first_appearance`: Where character is introduced
  - `chapter`: Chapter identifier
  - `section`: Section/heading name
  - `paragraph`: Paragraph number (0-indexed) within section
  - `context`: 1-2 sentence description
- `definition`: Clear statement of who character is
- `attributes`: Character-specific data
  - `occupation`: Job/role (can be "unspecified")
  - `age_range`: Approximate (e.g., "30s-40s", "elderly", "child")
  - `key_traits`: List of defining characteristics
  - `narrative_role`: What character does for the book
- `appearances`: All instances where character appears
  - `reference_type`: 
    - `full`: Character is focus, detailed treatment
    - `brief`: Character mentioned with some detail
    - `mention`: Passing reference only
  - `speaking_role`: Does character speak dialogue?
  - `primary_focus`: Is this appearance central to chapter?
- `relationships`: Connections to other entities
- `consistency_checks`: Track attribute consistency
  - Automated validation catches contradictions
- `tags`: Searchable labels
- `last_updated`: When entity last modified

---

### 2. Framework Schema
```json
{
  "entity_id": "framework-{slug}",
  "entity_type": "framework",
  "name": "Framework Name",
  "alternative_names": ["Alt Name 1", "Alt Name 2"],
  "first_appearance": {
    "chapter": "X",
    "section": "Section Name",
    "paragraph": 0,
    "context": "How introduced"
  },
  "definition": "Clear, one-sentence definition",
  "detailed_description": "Fuller explanation (2-3 paragraphs)",
  "components": [
    {
      "name": "Component Name",
      "description": "What this component does",
      "entity_id": "framework-component-{slug}"
    }
  ],
  "attributes": {
    "visual_form": "How to draw/visualize",
    "key_insight": "Core takeaway",
    "rally_ready": true,
    "shareable": true,
    "complexity_level": "low|medium|high"
  },
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "How used here",
      "reference_type": "definition|application|brief|mention",
      "development_stage": "introduction|expansion|synthesis|application"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "builds-on|contains|illustrated-by|opposes|synthesizes",
      "description": "Connection details"
    }
  ],
  "examples": [
    {
      "example_entity_id": "example-id",
      "chapter": "X",
      "purpose": "What example demonstrates"
    }
  ],
  "promises": [
    {
      "promise_text": "What was promised",
      "made_in_chapter": "X",
      "fulfilled_in_chapter": "Y|pending",
      "status": "fulfilled|pending|broken"
    }
  ],
  "consistency_rules": [
    {
      "rule": "Description of what must stay consistent",
      "examples": ["Example 1", "Example 2"]
    }
  ],
  "tags": ["core-framework", "ring-component", "diagnostic-tool"],
  "last_updated": "YYYY-MM-DD"
}
```

**Field Definitions:**

- `entity_id`: Format `framework-{slug}`
- `alternative_names`: Other ways this framework is referenced
- `definition`: Must be clear enough to remember
- `detailed_description`: Fuller context (for reference)
- `components`: Sub-elements if framework is composite
  - Each component can be its own entity
- `attributes`:
  - `visual_form`: Can it be drawn? How?
  - `rally_ready`: G+T appeal check
  - `shareable`: Would readers share this?
  - `complexity_level`: For sequencing/scaffolding
- `appearances`:
  - `reference_type`:
    - `definition`: Where formally defined
    - `application`: Where applied to example
    - `brief`: Quick reference
    - `mention`: Passing reference
  - `development_stage`: How framework evolves through book
- `examples`: Links to illustrative examples
- `consistency_rules`: What must never vary
  - e.g., "The Ring always has four habitats, never five"

---

### 3. Example Schema
```json
{
  "entity_id": "example-{slug}",
  "entity_type": "example",
  "name": "Example Name/Shorthand",
  "first_appearance": {
    "chapter": "X",
    "section": "Section Name",
    "paragraph": 0,
    "context": "How introduced"
  },
  "definition": "What this example shows",
  "attributes": {
    "domain": "family|safety|market|anarchy|hybrid",
    "stakes": "What's at risk/important",
    "real_or_hypothetical": "real|hypothetical|composite",
    "primary_framework": "framework-id",
    "complexity": "simple|moderate|complex"
  },
  "key_elements": [
    "Element 1",
    "Element 2"
  ],
  "critical_details": {
    "detail_type": "specific value that must stay consistent"
  },
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "How used here",
      "reference_type": "full|brief|mention",
      "purpose": "What this appearance demonstrates"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "illustrates|contrasts-with|builds-on",
      "description": "Connection"
    }
  ],
  "promises": [],
  "tags": ["recurring", "primary-example", "bookend"],
  "last_updated": "YYYY-MM-DD"
}
```

**Field Definitions:**

- `attributes`:
  - `domain`: Which habitat(s) this example involves
  - `stakes`: Why reader should care
  - `real_or_hypothetical`: Source type
  - `primary_framework`: Main framework illustrated
- `key_elements`: List of essential components
- `critical_details`: Specific facts that must stay consistent
  - e.g., for nail-maker: `{"original_production": "8 nails/day", "specialized_production": "10,000 nails/day"}`
- `tags`: Can include "bookend" if appears at start and end

---

### 4. Metaphor Schema
```json
{
  "entity_id": "metaphor-{slug}",
  "entity_type": "metaphor",
  "name": "Metaphor Name",
  "first_appearance": {
    "chapter": "X",
    "section": "Section Name",
    "paragraph": 0,
    "context": "How introduced"
  },
  "definition": "What this metaphor means",
  "attributes": {
    "represents": "What real concept this stands for",
    "key_qualities": ["Quality 1", "Quality 2"],
    "visual": "Can it be visualized?",
    "extends_across_chapters": true
  },
  "evolution": [
    {
      "chapter": "X",
      "development": "How metaphor develops/extends here"
    }
  ],
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "How used",
      "reference_type": "introduction|extension|application|mention"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "represents|pairs-with|contrasts",
      "description": "Connection"
    }
  ],
  "consistency_rules": [
    "Always lowercase except at sentence start",
    "Always paired with X metaphor"
  ],
  "tags": ["extended-metaphor", "ring-component"],
  "last_updated": "YYYY-MM-DD"
}
```

**Field Definitions:**

- `represents`: The actual concept this metaphor stands for
- `key_qualities`: What makes this metaphor work
- `evolution`: How metaphor develops through book
- `consistency_rules`: Usage conventions

---

### 5. Location Schema
```json
{
  "entity_id": "location-{slug}",
  "entity_type": "location",
  "name": "Location Name",
  "first_appearance": {
    "chapter": "X",
    "section": "Section Name",
    "paragraph": 0,
    "context": "How introduced"
  },
  "definition": "What/where this location is",
  "attributes": {
    "geographic_type": "real|fictional|conceptual",
    "specificity": "exact|general|symbolic",
    "role": "setting|symbol|both"
  },
  "geographic_details": {
    "city": "City name",
    "state": "State",
    "country": "Country",
    "coordinates": "If relevant"
  },
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "Scene set here",
      "reference_type": "full|brief|mention"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "setting-for|part-of",
      "description": "Connection"
    }
  ],
  "tags": ["recurring", "symbolic", "bookend"],
  "last_updated": "YYYY-MM-DD"
}
```

---

### 6. Claim Schema
```json
{
  "entity_id": "claim-{slug}",
  "entity_type": "claim",
  "name": "Short claim description",
  "first_appearance": {
    "chapter": "X",
    "section": "Section Name",
    "paragraph": 0,
    "context": "How stated"
  },
  "claim_text": "Exact wording of claim",
  "claim_type": "factual|argumentative|definitional",
  "attributes": {
    "verifiable": true,
    "source_required": false,
    "centrality": "core|supporting|minor"
  },
  "evidence": [
    {
      "type": "citation|data|example",
      "description": "Supporting evidence",
      "source": "Where it comes from"
    }
  ],
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "How restated",
      "wording_variation": "If reworded differently"
    }
  ],
  "consistency_checks": [
    {
      "claim_version": "Wording found",
      "chapter": "X",
      "status": "consistent|inconsistent",
      "notes": "Details if inconsistent"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "supports|contradicts|refines",
      "description": "Connection"
    }
  ],
  "tags": ["requires-verification", "core-argument"],
  "last_updated": "YYYY-MM-DD"
}
```

**Field Definitions:**

- `claim_type`:
  - `factual`: Verifiable fact (e.g., "The Pentagon has HOV lanes")
  - `argumentative`: Book's argument (e.g., "Markets generate surplus")
  - `definitional`: How we define terms (e.g., "Capitalism = markets at scale")
- `evidence`: Supporting material
- `consistency_checks`: Track if claim is restated consistently

---

### 7. Promise Schema
```json
{
  "entity_id": "promise-{slug}",
  "entity_type": "promise",
  "name": "Promise description",
  "first_appearance": {
    "chapter": "X",
    "section": "Section Name",
    "paragraph": 0,
    "context": "How promise is made"
  },
  "promise_text": "Exact wording",
  "promise_type": "forward-reference|payoff|structural|thematic",
  "attributes": {
    "specificity": "exact|general",
    "urgency": "immediate|delayed|distant",
    "stakes": "high|medium|low"
  },
  "fulfillment": {
    "status": "fulfilled|pending|broken",
    "fulfilled_in_chapter": "Y",
    "fulfilled_by": ["entity-id-1", "entity-id-2"],
    "fulfillment_quality": "complete|partial|unsatisfactory",
    "notes": "How promise was fulfilled or why not"
  },
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "paragraph": 0,
      "context": "Where referenced",
      "reference_type": "made|referenced|fulfilled"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "entity-id",
      "relationship_type": "fulfilled-by|depends-on",
      "description": "Connection"
    }
  ],
  "reader_impact": {
    "creates_expectation": true,
    "sustains_engagement": true,
    "critical_to_satisfaction": false
  },
  "tags": ["structural-promise", "major-payoff"],
  "last_updated": "YYYY-MM-DD"
}
```

**Field Definitions:**

- `promise_type`:
  - `forward-reference`: "We'll return to X"
  - `payoff`: "Chapter Y will deliver Z"
  - `structural`: Promise about book structure
  - `thematic`: Promise about emotional arc
- `fulfillment`: Detailed tracking
  - `status`: Current state
  - `fulfilled_by`: Which entities delivered on promise
  - `fulfillment_quality`: How well was it fulfilled
- `reader_impact`: Why this promise matters

---

## RELATIONSHIPS STRUCTURE

### Relationship Types

**Stored in top-level `relationships` array for easy querying:**
```json
{
  "relationships": [
    {
      "relationship_id": "rel-{unique-id}",
      "source_entity_id": "entity-1",
      "target_entity_id": "entity-2",
      "relationship_type": "type",
      "bidirectional": false,
      "description": "How they connect",
      "strength": "strong|moderate|weak",
      "chapters": ["1", "5", "9"],
      "created_date": "YYYY-MM-DD"
    }
  ]
}
```

**Relationship Types by Category:**

**Illustrative:**
- `illustrates`: Example → Framework
- `demonstrates`: Example → Concept
- `exemplifies`: Character → Principle

**Structural:**
- `builds-on`: Framework B builds on Framework A
- `contains`: Framework contains Component
- `part-of`: Component is part of Framework
- `synthesizes`: Framework C synthesizes A + B

**Oppositional:**
- `contrasts-with`: Entity A vs Entity B
- `contradicts`: Claim A contradicts Claim B
- `opposes`: Character/concept opposition

**Developmental:**
- `evolves-into`: Early version → Later version
- `refines`: Later statement refines earlier
- `extends`: Metaphor extension

**Fulfillment:**
- `fulfilled-by`: Promise fulfilled by Entity
- `payoff-for`: Entity is payoff for Promise

**Narrative:**
- `setting-for`: Location is setting for Event
- `features`: Example features Character
- `appears-in`: Character appears in Example

---

### Relationship Strength

**Strong:** Critical to understanding
- Framework → Core Component
- Primary Example → Framework
- Major Promise → Fulfillment

**Moderate:** Important but not critical
- Supporting Example → Framework
- Character → Secondary Framework
- Metaphor → Related Metaphor

**Weak:** Tangential or passing
- Mention of Example in unrelated context
- Character briefly references Framework
- Location mentioned without significance

---

## INDEXES

### Purpose of Indexes

**Fast lookup without scanning entire entity array**

Indexes rebuild automatically when entities added/modified.

---

### Index Structure
```json
{
  "indexes": {
    "by_type": {
      "character": ["char-sarah", "char-maya", "char-acura-driver"],
      "framework": ["framework-ring", "framework-compass"],
      "example": ["example-slug-line", "example-nail-maker"],
      "metaphor": ["metaphor-engine", "metaphor-shell"],
      "location": ["location-pentagon", "location-crystal-city"],
      "claim": ["claim-ring-has-four-habitats"],
      "promise": ["promise-ch9-complete-framework"]
    },
    
    "by_chapter": {
      "prologue": {
        "characters": ["char-acura-driver"],
        "frameworks": ["framework-ring"],
        "examples": ["example-slug-line"],
        "locations": ["location-pentagon", "location-crystal-city"]
      },
      "1": {
        "frameworks": ["framework-ring"],
        "examples": ["example-family-performance-review"]
      }
      // ... for each chapter
    },
    
    "by_name": {
      "sarah": "char-sarah",
      "the ring": "framework-ring",
      "slug line": "example-slug-line",
      "pentagon": "location-pentagon"
    },
    
    "by_tag": {
      "core-framework": ["framework-ring", "framework-compass"],
      "recurring": ["example-slug-line", "char-sarah"],
      "bookend": ["example-slug-line", "location-pentagon"],
      "requires-verification": ["claim-fusion-timeline"]
    }
  }
}
```

---

## VALIDATION RULES

### Entity Validation

**Every entity must pass these checks before being added:**
```javascript
{
  "validation_rules": {
    "all_entities": [
      "entity_id must be unique",
      "entity_id must match format: {type}-{slug}",
      "entity_type must be valid type",
      "name cannot be empty",
      "first_appearance.chapter must be valid chapter",
      "last_updated must be ISO date"
    ],
    
    "characters": [
      "Must have occupation (can be 'unspecified')",
      "Must have narrative_role defined",
      "Must have at least one appearance"
    ],
    
    "frameworks": [
      "Must have clear definition",
      "Must have at least one appearance",
      "Alternative_names must be array (can be empty)",
      "Components must reference valid entities or be inline"
    ],
    
    "examples": [
      "Must have domain specified",
      "Must have primary_framework linked",
      "Must have at least one appearance",
      "If critical_details present, must track in consistency_checks"
    ],
    
    "promises": [
      "Must have fulfillment status",
      "If status='fulfilled', must have fulfilled_in_chapter",
      "If status='fulfilled', must have fulfilled_by array"
    ]
  }
}
```

---

### Relationship Validation
```javascript
{
  "relationship_validation": [
    "source_entity_id must exist in entities array",
    "target_entity_id must exist in entities array",
    "relationship_type must be valid type",
    "If bidirectional=true, reverse relationship should exist",
    "chapters list should match where entities co-appear"
  ]
}
```

---

### Consistency Validation

**Automated checks run on full database:**
```javascript
{
  "consistency_checks": [
    {
      "check_type": "entity_reference",
      "description": "All entity_ids referenced in relationships must exist",
      "auto_fix": false
    },
    {
      "check_type": "promise_fulfillment",
      "description": "All promises should be fulfilled or explicitly pending",
      "auto_fix": false
    },
    {
      "check_type": "appearance_count",
      "description": "Entity appearances array should match actual chapter content",
      "auto_fix": false
    },
    {
      "check_type": "duplicate_detection",
      "description": "No two entities should have identical names",
      "auto_fix": false
    },
    {
      "check_type": "orphan_detection",
      "description": "Major entities should have at least one relationship",
      "auto_fix": false
    }
  ]
}
```

---

## QUERY PATTERNS

### Common Query Operations

**How agents access the knowledge graph:**

---

### Query 1: Get Entity by ID
```javascript
// Sonnet needs details about Sarah
function getEntity(entityId) {
  return database.entities.find(e => e.entity_id === entityId);
}

// Usage:
const sarah = getEntity('char-sarah');
console.log(sarah.attributes.occupation);
```

---

### Query 2: Get All Entities of Type
```javascript
// Opus wants all frameworks to validate consistency
function getEntitiesByType(type) {
  return database.entities.filter(e => e.entity_type === type);
}

// Usage:
const allFrameworks = getEntitiesByType('framework');
```

---

### Query 3: Get Entities by Chapter
```javascript
// Sonnet writing Ch 10, needs entities already established
function getEntitiesByChapter(chapter) {
  return database.indexes.by_chapter[chapter];
}

// Usage:
const ch9Entities = getEntitiesByChapter('9');
```

---

### Query 4: Get Related Entities
```javascript
// Find all examples that illustrate The Ring
function getRelatedEntities(entityId, relationshipType = null) {
  let relationships = database.relationships.filter(
    r => r.source_entity_id === entityId
  );
  
  if (relationshipType) {
    relationships = relationships.filter(
      r => r.relationship_type === relationshipType
    );
  }
  
  return relationships.map(r => getEntity(r.target_entity_id));
}

// Usage:
const ringExamples = getRelatedEntities('framework-ring', 'illustrates');
```

---

### Query 5: Get Unfulfilled Promises
```javascript
// Claude.ai checks what promises are still pending
function getUnfulfilledPromises() {
  return database.entities.filter(
    e => e.entity_type === 'promise' && 
         e.fulfillment.status === 'pending'
  );
}

// Usage:
const pendingPromises = getUnfulfilledPromises();
```

---

### Query 6: Find Entity by Name (Fuzzy)
```javascript
// Sonnet searches for "ring" → might be "The Ring" framework
function findByName(searchTerm) {
  const normalized = searchTerm.toLowerCase();
  
  // Check index first (exact match)
  if (database.indexes.by_name[normalized]) {
    return getEntity(database.indexes.by_name[normalized]);
  }
  
  // Fuzzy search in entity names
  return database.entities.filter(e => 
    e.name.toLowerCase().includes(normalized) ||
    (e.alternative_names && e.alternative_names.some(
      alt => alt.toLowerCase().includes(normalized)
    ))
  );
}

// Usage:
const ringMatches = findByName('ring');
```

---

### Query 7: Consistency Check for Attribute
```javascript
// Opus validates that Maya's job title is consistent
function checkAttributeConsistency(entityId, attributePath) {
  const entity = getEntity(entityId);
  const checks = entity.consistency_checks || [];
  
  return checks.filter(c => c.attribute === attributePath);
}

// Usage:
const mayaJobConsistency = checkAttributeConsistency(
  'char-maya',
  'occupation'
);
```

---

## UPDATE PROTOCOLS

### Adding New Entity

**Workflow:**

1. **Opus extracts entity** from chapter
2. **Validates against schema**
3. **Checks for duplicates** (by name, by similar definition)
4. **Assigns unique ID** following format
5. **Adds to entities array**
6. **Creates relationships** (if any)
7. **Updates indexes** (automatic rebuild)
8. **Logs in validation_log**
9. **Increments metadata.total_entities**
10. **Updates metadata.last_updated**

**Validation Steps:**
```javascript
function addEntity(newEntity) {
  // 1. Validate schema
  if (!validateEntitySchema(newEntity)) {
    throw new Error('Invalid entity schema');
  }
  
  // 2. Check for duplicates
  const duplicate = findByName(newEntity.name);
  if (duplicate.length > 0) {
    console.warn('Possible duplicate:', duplicate);
    // Manual review required
  }
  
  // 3. Ensure unique ID
  if (database.entities.some(e => e.entity_id === newEntity.entity_id)) {
    throw new Error('Entity ID already exists');
  }
  
  // 4. Add entity
  database.entities.push(newEntity);
  
  // 5. Update indexes
  rebuildIndexes();
  
  // 6. Update metadata
  database.metadata.total_entities++;
  database.metadata.last_updated = new Date().toISOString().split('T')[0];
  
  // 7. Log
  database.validation_log.push({
    action: 'entity_added',
    entity_id: newEntity.entity_id,
    timestamp: new Date().toISOString(),
    agent: 'opus-4.5'
  });
  
  return newEntity.entity_id;
}
```

---

### Updating Existing Entity

**Workflow:**

1. **Retrieve entity** by ID
2. **Create backup** of current state (in validation_log)
3. **Apply modifications**
4. **Validate updated entity**
5. **Update last_updated timestamp**
6. **Rebuild indexes** if necessary
7. **Log change**
```javascript
function updateEntity(entityId, updates) {
  const entity = getEntity(entityId);
  if (!entity) {
    throw new Error('Entity not found');
  }
  
  // Backup current state
  database.validation_log.push({
    action: 'entity_updated',
    entity_id: entityId,
    previous_state: JSON.parse(JSON.stringify(entity)),
    timestamp: new Date().toISOString(),
    agent: 'sonnet-4.5'
  });
  
  // Apply updates
  Object.assign(entity, updates);
  entity.last_updated = new Date().toISOString().split('T')[0];
  
  // Validate
  if (!validateEntitySchema(entity)) {
    // Rollback
    throw new Error('Update would violate schema');
  }
  
  // Rebuild indexes if name changed
  if (updates.name) {
    rebuildIndexes();
  }
  
  return entity;
}
```

---

### Adding Relationship
```javascript
function addRelationship(sourceId, targetId, type, description) {
  // Validate entities exist
  if (!getEntity(sourceId) || !getEntity(targetId)) {
    throw new Error('One or both entities not found');
  }
  
  // Create relationship
  const relationship = {
    relationship_id: `rel-${generateUniqueId()}`,
    source_entity_id: sourceId,
    target_entity_id: targetId,
    relationship_type: type,
    bidirectional: false,
    description: description,
    strength: 'moderate',
    chapters: [],
    created_date: new Date().toISOString().split('T')[0]
  };
  
  // Add to database
  database.relationships.push(relationship);
  
  // Also add to source entity's relationships array
  const sourceEntity = getEntity(sourceId);
  sourceEntity.relationships.push({
    related_entity_id: targetId,
    relationship_type: type,
    description: description
  });
  
  return relationship.relationship_id;
}
```

---

## VERSIONING

### Schema Versioning

**Current Version:** 1.0.0

**Version Format:** MAJOR.MINOR.PATCH

- **MAJOR:** Breaking changes to schema structure
- **MINOR:** New entity types or fields (backward compatible)
- **PATCH:** Bug fixes, clarifications

**Migration Protocol:**

When schema version changes:
1. Create migration script
2. Backup current database
3. Apply transformations
4. Validate all entities against new schema
5. Update `metadata.schema_version`

---

### Entity Versioning

**Entities don't version independently**, but changes are logged:
```json
{
  "validation_log": [
    {
      "action": "entity_updated",
      "entity_id": "char-sarah",
      "previous_state": { /* full entity state */ },
      "timestamp": "2026-01-10T14:30:00Z",
      "agent": "sonnet-4.5",
      "reason": "Corrected occupation detail"
    }
  ]
}
```

**This enables:**
- Audit trail of all changes
- Rollback capability
- Understanding why entity changed

---

## EXAMPLE DATABASE SNAPSHOT

### Minimal Working Example
```json
{
  "metadata": {
    "schema_version": "1.0.0",
    "last_updated": "2026-01-10",
    "total_entities": 3,
    "manuscript_version": "draft",
    "extraction_complete": false
  },
  
  "entities": [
    {
      "entity_id": "char-sarah",
      "entity_type": "character",
      "name": "Sarah",
      "first_appearance": {
        "chapter": "9",
        "section": "Opening: I See the Ring, Now What?",
        "paragraph": 0,
        "context": "Standing in break room, frustrated"
      },
      "definition": "Professional who sees the Ring but doesn't know what to do",
      "attributes": {
        "occupation": "unspecified",
        "narrative_role": "Reader proxy for Ch 9"
      },
      "appearances": [
        {
          "chapter": "9",
          "section": "Opening",
          "reference_type": "full"
        }
      ],
      "relationships": [
        {
          "related_entity_id": "framework-ring",
          "relationship_type": "illustrates",
          "description": "Exemplifies someone who has diagnostic clarity but needs action framework"
        }
      ],
      "tags": ["reader-proxy"],
      "last_updated": "2026-01-10"
    },
    
    {
      "entity_id": "framework-ring",
      "entity_type": "framework",
      "name": "The Ring",
      "alternative_names": ["Four Habitats model", "The Loop"],
      "first_appearance": {
        "chapter": "prologue",
        "section": "The Ring in View",
        "paragraph": 0,
        "context": "First glimpsed in slug line experience"
      },
      "definition": "Model showing four habitats (Family, Safety, Markets, Friendship) as interdependent systems, not rival ideologies",
      "components": [
        {
          "name": "Family/Communism",
          "description": "Intimate scale, from-each-to-each logic"
        },
        {
          "name": "Safety/Socialism",
          "description": "Collective essentials, impartial protection"
        },
        {
          "name": "Markets/Capitalism",
          "description": "Surplus engine, individual value at scale"
        },
        {
          "name": "Friendship/Anarchy",
          "description": "Voluntary cooperation, emergent order"
        }
      ],
      "attributes": {
        "visual_form": "Circular, not linear",
        "rally_ready": true,
        "shareable": true
      },
      "appearances": [
        {
          "chapter": "prologue",
          "reference_type": "brief"
        },
        {
          "chapter": "2",
          "reference_type": "definition"
        },
        {
          "chapter": "6",
          "reference_type": "synthesis"
        }
      ],
      "consistency_rules": [
        {
          "rule": "Always capitalize 'The Ring'",
          "examples": ["The Ring consists of...", "when the Ring turns..."]
        },
        {
          "rule": "Always four habitats, never five",
          "examples": []
        }
      ],
      "tags": ["core-framework"],
      "last_updated": "2026-01-10"
    },
    
    {
      "entity_id": "example-slug-line",
      "entity_type": "example",
      "name": "Slug Line / Pentagon Commute",
      "first_appearance": {
        "chapter": "prologue",
        "section": "Opening scene",
        "paragraph": 0,
        "context": "Joshua's ride home after witching hour"
      },
      "definition": "Informal carpool showing all four habitats cooperating",
      "attributes": {
        "domain": "hybrid",
        "primary_framework": "framework-ring",
        "real_or_hypothetical": "real"
      },
      "critical_details": {
        "witching_hour": "6pm",
        "location_start": "Crystal City",
        "location_end": "Tackett's Mill",
        "vehicle": "green Acura"
      },
      "appearances": [
        {
          "chapter": "prologue",
          "reference_type": "full"
        },
        {
          "chapter": "2",
          "reference_type": "brief"
        },
        {
          "chapter": "7",
          "reference_type": "full"
        },
        {
          "chapter": "epilogue",
          "reference_type": "full"
        }
      ],
      "relationships": [
        {
          "related_entity_id": "framework-ring",
          "relationship_type": "illustrates",
          "description": "Primary example of Ring in action"
        }
      ],
      "tags": ["recurring", "primary-example", "bookend"],
      "last_updated": "2026-01-10"
    }
  ],
  
  "relationships": [
    {
      "relationship_id": "rel-001",
      "source_entity_id": "example-slug-line",
      "target_entity_id": "framework-ring",
      "relationship_type": "illustrates",
      "description": "Slug line is primary example of Ring",
      "strength": "strong",
      "chapters": ["prologue", "2", "7", "epilogue"],
      "created_date": "2026-01-10"
    },
    {
      "relationship_id": "rel-002",
      "source_entity_id": "char-sarah",
      "target_entity_id": "framework-ring",
      "relationship_type": "illustrates",
      "description": "Sarah exemplifies transition from seeing Ring to acting",
      "strength": "moderate",
      "chapters": ["9"],
      "created_date": "2026-01-10"
    }
  ],
  
  "indexes": {
    "by_type": {
      "character": ["char-sarah"],
      "framework": ["framework-ring"],
      "example": ["example-slug-line"]
    },
    "by_chapter": {
      "prologue": {
        "frameworks": ["framework-ring"],
        "examples": ["example-slug-line"]
      },
      "9": {
        "characters": ["char-sarah"]
      }
    },
    "by_name": {
      "sarah": "char-sarah",
      "the ring": "framework-ring",
      "slug line": "example-slug-line"
    },
    "by_tag": {
      "core-framework": ["framework-ring"],
      "bookend": ["example-slug-line"],
      "reader-proxy": ["char-sarah"]
    }
  },
  
  "validation_log": [
    {
      "action": "database_initialized",
      "timestamp": "2026-01-10T12:00:00Z",
      "agent": "opus-4.5"
    },
    {
      "action": "entity_added",
      "entity_id": "framework-ring",
      "timestamp": "2026-01-10T12:05:00Z",
      "agent": "opus-4.5"
    },
    {
      "action": "entity_added",
      "entity_id": "example-slug-line",
      "timestamp": "2026-01-10T12:10:00Z",
      "agent": "opus-4.5"
    },
    {
      "action": "entity_added",
      "entity_id": "char-sarah",
      "timestamp": "2026-01-10T12:15:00Z",
      "agent": "opus-4.5"
    }
  ]
}
```

---

## INTEGRATION WITH WORKFLOW

### How Schema Supports Multi-Agent System

**Opus 4.5 (Structure + Validation):**
- Extracts entities from manuscript
- Validates against schema
- Checks consistency
- Updates knowledge graph
- **Uses:** Entity schemas, validation rules, query patterns

**Sonnet 4.5 (Content Generation):**
- Queries existing entities before writing
- Maintains consistency with established entities
- References entities correctly
- Flags new entities created during writing
- **Uses:** Query patterns, entity data, relationship data

**Claude.ai Project (Orchestration):**
- Manages master knowledge graph
- Merges updates from Opus and Sonnet
- Runs consistency checks across full database
- Tracks promise fulfillment
- **Uses:** All schemas, validation logs, complete database

---

## FINAL NOTES

**This schema is the technical foundation for manuscript quality control.**

**Key Principles:**
1. **Structured but flexible** - room to grow
2. **Validation-first** - catch errors early
3. **Relationship-rich** - entities connect meaningfully
4. **Query-optimized** - fast agent access
5. **Auditable** - every change logged
6. **Consistent** - same structure throughout

**When implemented correctly, this enables:**
- ✅ Zero continuity errors
- ✅ All promises tracked and fulfilled
- ✅ Consistent entity treatment across 10+ chapters
- ✅ Fast agent queries during content generation
- ✅ Quality validation at every step

---

**Next foundation document: STYLE_GUIDELINES.md (defines voice, tone, formatting rules for consistent G+T-optimized writing)?**