# ENTITY EXTRACTION GUIDE
**Purpose:** How Opus 4.5 extracts entities from manuscript to build knowledge graph  
**Last Updated:** January 10, 2026

---

## WHAT IS ENTITY EXTRACTION?

### The Problem

As we write a book with:
- 10+ chapters
- Recurring characters/examples
- Interconnected frameworks
- Cross-chapter references
- Cumulative argument

**We need to track:**
- Who appears where
- Which frameworks build on which
- What examples reappear
- What promises need payoff
- What definitions must stay consistent

**Without systematic tracking, we get:**
- Inconsistent character details
- Forgotten promises
- Contradictory frameworks
- Orphaned examples
- Continuity errors

---

### The Solution: Knowledge Graph

**A structured database of every important entity in the book.**

**Entity = any named concept, character, example, or framework that:**
1. Appears in the manuscript
2. Needs consistent treatment
3. May reappear later
4. Connects to other entities

**The knowledge graph enables:**
- ✅ Continuity checking across chapters
- ✅ Entity relationship mapping
- ✅ Promise tracking (if we mention X in Ch 2, it better pay off by Ch 8)
- ✅ Consistency validation (Sarah's job title stays the same)
- ✅ Cross-reference detection (which chapters use slug line?)

---

## ENTITY TYPES

### Type 1: CHARACTERS

**Definition:** Named individuals who appear in examples/stories

**Examples in our book:**
- Sarah (break room, Chapter 9)
- Maya (hospital algorithm, Chapter 10)
- The Acura driver (slug line, Prologue)
- Retired teacher at city council (Chapter 7 example)

**What to Extract:**
- Name
- First appearance (chapter + context)
- Role/occupation
- Key characteristics
- All appearances across chapters
- Relationship to frameworks (which framework does this character illustrate?)

**Why It Matters:**
If Sarah appears in Ch 9 as "marketing manager" and Ch 10 as "software engineer," readers notice. Consistency requires tracking.

---

### Type 2: FRAMEWORKS

**Definition:** Named conceptual models that structure the book's argument

**Examples in our book:**
- The Ring
- Four Habitats
- Ring Compass
- Obligation to Excess
- Jobs to Be Done

**What to Extract:**
- Framework name (exact wording)
- First introduction (chapter + context)
- Formal definition
- Components/sub-elements
- Relationship to other frameworks
- All applications/references
- Visual representation (if any)

**Why It Matters:**
Frameworks are the book's skeleton. If "The Ring" is defined differently in Ch 2 vs Ch 7, the argument collapses.

---

### Type 3: EXAMPLES

**Definition:** Concrete illustrations used to demonstrate frameworks

**Examples in our book:**
- Slug line (Pentagon commute)
- Family performance review
- Hospital algorithm (Maya's story)
- Communist Christmas
- Nietzsche's horse
- Nicaragua mother/child

**What to Extract:**
- Example name/shorthand
- First appearance
- Full vs. brief mentions
- Framework illustrated
- Domain (family/market/safety/anarchy)
- Stakes/purpose
- All references across chapters

**Why It Matters:**
Examples should reappear for reinforcement. "The slug line" gets introduced in Prologue, referenced in Ch 2, analyzed in Ch 7. Tracking ensures we don't orphan examples.

---

### Type 4: METAPHORS

**Definition:** Extended comparisons that carry meaning across chapters

**Examples in our book:**
- "The engine" (capitalism as surplus generator)
- "The shell" (safety commons protecting everything)
- "Planting trees" (long-game thinking)
- "Fishing knowledge" (teaching principles not steps)
- "The ring turning" (habitats in motion)

**What to Extract:**
- Metaphor name
- First introduction
- What it represents
- How it evolves across chapters
- All uses

**Why It Matters:**
Metaphors create cohesion. If we introduce "the engine" in Ch 5 but never use it again, we've wasted setup. If we use it in Ch 10 without establishing it first, readers are lost.

---

### Type 5: LOCATIONS

**Definition:** Physical or conceptual places that recur

**Examples in our book:**
- Pentagon commuter lot
- Crystal City
- Tackett's Mill
- Sarah's break room
- Maya's hospital network

**What to Extract:**
- Location name
- First appearance
- Geographic/conceptual description
- Role in narrative
- All appearances

**Why It Matters:**
Returning to locations creates familiarity. The Pentagon lot in Prologue → referenced in Epilogue creates bookend symmetry.

---

### Type 6: CLAIMS/ASSERTIONS

**Definition:** Specific factual or argumentative claims that need consistency

**Examples in our book:**
- "Claude's knowledge cutoff is January 2025"
- "The nail-maker goes from 8 to 10,000 nails/day"
- "The Ring has four habitats, not five"
- "G+T readers are our target audience"

**What to Extract:**
- Claim text (exact wording if possible)
- First statement
- Supporting evidence (if any)
- All restatements
- Contradictions (flag for resolution)

**Why It Matters:**
If we say "10,000 nails" in Ch 5 and "8,000 nails" in Ch 9, readers catch it. Claims must stay consistent.

---

### Type 7: PROMISES

**Definition:** Forward references that create expectation

**Examples in our book:**
- "We'll return to the slug line in Chapter 7"
- "Chapter 9 will show you what to do with this insight"
- "The Epilogue reveals what becomes possible"

**What to Extract:**
- Promise text
- Where made (chapter)
- What's promised
- Where fulfilled (chapter)
- Status (fulfilled/pending/broken)

**Why It Matters:**
Broken promises frustrate readers. "We'll return to X" must actually return to X. This is payoff tracking.

---

## EXTRACTION CRITERIA

### What Qualifies as an Entity?

**Extract if:**
- ✅ Has a specific name (not generic "a manager" but "Sarah")
- ✅ Appears more than once OR will appear later
- ✅ Requires consistent treatment
- ✅ Connects to framework/argument
- ✅ Creates reader expectation

**Do NOT extract:**
- ❌ Generic references ("a friend," "some people")
- ❌ One-time minor mentions with no future relevance
- ❌ Common knowledge (no need to track "coffee" or "Tuesday")
- ❌ Purely transitional phrases

---

### Examples: Extract vs. Skip

**EXTRACT:**
- ✅ "Sarah stood in the break room..." (named character)
- ✅ "The Ring consists of four habitats..." (framework)
- ✅ "The slug line at the Pentagon..." (recurring example)
- ✅ "Obligation to excess means..." (key concept)

**SKIP:**
- ❌ "A person might think..." (generic)
- ❌ "On Tuesday morning..." (time reference, not entity)
- ❌ "Someone once said..." (no name, no recurrence)
- ❌ "In one study..." (unless we reference this study multiple times)

---

## EXTRACTION PROCESS (Step-by-Step)

### Phase 1: Initial Read-Through

**Objective:** Identify all potential entities

**Steps:**
1. Read chapter completely (don't extract while reading)
2. Note named concepts, characters, examples
3. Flag anything that might recur
4. Mark forward promises
5. Identify framework definitions

**Output:** Rough list of entities to extract

---

### Phase 2: Detailed Extraction

**Objective:** Extract complete entity data

**For Each Entity:**

1. **Classify Type**
   - Character, Framework, Example, Metaphor, Location, Claim, or Promise?

2. **Extract Core Data**
   - Name (exact as it appears)
   - First appearance (chapter number + paragraph/section)
   - Definition/description
   - Role/purpose

3. **Map Relationships**
   - Which frameworks does this connect to?
   - Which other entities does it reference?
   - What prior entities does it build on?

4. **Track Appearances**
   - List every mention (chapter + context)
   - Note whether full treatment or brief reference

5. **Flag Considerations**
   - Consistency checks needed?
   - Promises requiring payoff?
   - Potential contradictions with existing entities?

---

### Phase 3: JSON Formatting

**Objective:** Structure data for knowledge graph

**Standard Entity Format:**
```json
{
  "entity_id": "unique-identifier",
  "entity_type": "character|framework|example|metaphor|location|claim|promise",
  "name": "Entity Name",
  "first_appearance": {
    "chapter": "prologue|1-10|epilogue|appendix",
    "section": "Opening Scene",
    "context": "Brief description of first mention"
  },
  "definition": "Clear, concise definition or description",
  "attributes": {
    "key": "value"
  },
  "appearances": [
    {
      "chapter": "X",
      "section": "Section Name",
      "context": "How entity appears here",
      "reference_type": "full|brief|mention"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "other-entity-id",
      "relationship_type": "illustrates|builds-on|contradicts|references",
      "description": "How they connect"
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
  "consistency_notes": "Any variations or potential issues",
  "last_updated": "YYYY-MM-DD"
}
```

---

### Phase 4: Validation

**Objective:** Ensure extraction quality

**Checklist:**
- [ ] Entity type correctly classified?
- [ ] Name exactly as it appears in manuscript?
- [ ] Definition clear and accurate?
- [ ] All appearances tracked?
- [ ] Relationships mapped?
- [ ] Promises identified?
- [ ] Consistency checked against existing entities?
- [ ] JSON valid (no syntax errors)?

---

## DETAILED ENTITY SCHEMAS

### Character Entity
```json
{
  "entity_id": "char-sarah",
  "entity_type": "character",
  "name": "Sarah",
  "first_appearance": {
    "chapter": "9",
    "section": "Opening: I See the Ring, Now What?",
    "context": "Standing in break room, frustrated about seeing the ring but not knowing what to do"
  },
  "definition": "Mid-level professional who has learned to see the Ring but feels paralyzed about how to act",
  "attributes": {
    "occupation": "Not specified (works in company with dysfunctional family/market hybrid)",
    "age_range": "Implied 30s-40s",
    "key_traits": "Frustrated, intelligent, sees patterns, wants agency",
    "narrative_role": "Reader proxy for transition from diagnosis to action"
  },
  "appearances": [
    {
      "chapter": "9",
      "section": "Opening",
      "context": "Main character, break room scene",
      "reference_type": "full"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "framework-ring",
      "relationship_type": "illustrates",
      "description": "Sarah exemplifies someone who has learned to see the Ring but needs the internal framework"
    },
    {
      "related_entity_id": "framework-compass",
      "relationship_type": "uses",
      "description": "Implicit user of Ring Compass to diagnose her workplace"
    }
  ],
  "promises": [],
  "consistency_notes": "Occupation deliberately vague to allow reader projection. Keep it that way.",
  "last_updated": "2026-01-10"
}
```

---

### Framework Entity
```json
{
  "entity_id": "framework-ring",
  "entity_type": "framework",
  "name": "The Ring",
  "first_appearance": {
    "chapter": "prologue",
    "section": "The Ring in View",
    "context": "First mentioned as pattern Joshua sees in slug line experience"
  },
  "definition": "A model showing four habitats (Family/Communism, Safety/Socialism, Markets/Capitalism, Friendship/Anarchy) operating as interdependent systems at different scales, not rival ideologies",
  "attributes": {
    "components": [
      "Family/Communism habitat",
      "Safety Commons/Socialism habitat", 
      "Markets/Capitalism habitat",
      "Friendship/Anarchy habitat"
    ],
    "visual_form": "Circular/ring structure (not linear left/right)",
    "key_insight": "Different systems for different scales, not competing ideologies",
    "alternative_names": ["The Loop", "Four Habitats model"]
  },
  "appearances": [
    {
      "chapter": "prologue",
      "section": "The Ring in View",
      "context": "First introduction",
      "reference_type": "brief"
    },
    {
      "chapter": "2",
      "section": "Final section",
      "context": "Explicitly named and previewed",
      "reference_type": "full"
    },
    {
      "chapter": "6",
      "section": "Closing",
      "context": "Ring complete after all four habitats introduced",
      "reference_type": "full"
    },
    {
      "chapter": "7",
      "section": "Throughout",
      "context": "Ring turning in hybrids",
      "reference_type": "full"
    },
    {
      "chapter": "8",
      "section": "Ring Compass development",
      "context": "Ring as foundation for navigation tool",
      "reference_type": "full"
    },
    {
      "chapter": "epilogue",
      "section": "Multiple references",
      "context": "Ring operating smoothly in future vision",
      "reference_type": "brief"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "framework-compass",
      "relationship_type": "builds-on",
      "description": "Ring Compass is navigation tool built on Ring foundation"
    },
    {
      "related_entity_id": "example-slug-line",
      "relationship_type": "illustrated-by",
      "description": "Slug line is primary example showing Ring in action"
    },
    {
      "related_entity_id": "metaphor-ring-turning",
      "relationship_type": "generates",
      "description": "Ring imagery creates 'ring turning' metaphor"
    }
  ],
  "promises": [
    {
      "promise_text": "We'll redraw the map to show how these systems actually relate",
      "made_in_chapter": "2",
      "fulfilled_in_chapter": "6",
      "status": "fulfilled"
    }
  ],
  "consistency_notes": "Always capitalize 'The Ring'. Four habitats, never five. Ring is circular, not linear. Each habitat has two names (Family/Communism, etc.).",
  "last_updated": "2026-01-10"
}
```

---

### Example Entity
```json
{
  "entity_id": "example-slug-line",
  "entity_type": "example",
  "name": "Slug Line / Pentagon Commute",
  "first_appearance": {
    "chapter": "prologue",
    "section": "Opening scene",
    "context": "Joshua's ride home from Pentagon after witching hour"
  },
  "definition": "Informal carpool system outside Pentagon where strangers share rides to access HOV lanes, demonstrating how all four habitats cooperate in one system",
  "attributes": {
    "location": "Crystal City / Pentagon area, Northern Virginia",
    "key_elements": [
      "HOV lane rules (public policy)",
      "Private cars (market)",
      "Voluntary coordination (anarchy)",
      "Generosity after witching hour (family-like)"
    ],
    "stakes": "How does a 'shouldn't work' system actually function?",
    "framework_illustrated": "The Ring - all four habitats at once"
  },
  "appearances": [
    {
      "chapter": "prologue",
      "section": "Entire chapter",
      "context": "Primary narrative",
      "reference_type": "full"
    },
    {
      "chapter": "1",
      "section": "Closing",
      "context": "Brief callback to 'ride that shouldn't have worked'",
      "reference_type": "brief"
    },
    {
      "chapter": "2",
      "section": "When the Line Meets the Parking Lot",
      "context": "Analyzed through left/right line failure",
      "reference_type": "full"
    },
    {
      "chapter": "7",
      "section": "The Ring in the Parking Lot",
      "context": "Detailed hybrid analysis",
      "reference_type": "full"
    },
    {
      "chapter": "epilogue",
      "section": "Opening scene",
      "context": "Bookend - return to green Acura",
      "reference_type": "full"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "framework-ring",
      "relationship_type": "illustrates",
      "description": "Primary example of Ring in action"
    },
    {
      "related_entity_id": "char-acura-driver",
      "relationship_type": "features",
      "description": "Driver's generosity is key moment"
    },
    {
      "related_entity_id": "location-pentagon",
      "relationship_type": "takes-place",
      "description": "Setting for example"
    }
  ],
  "promises": [
    {
      "promise_text": "This ride will show us something important about systems",
      "made_in_chapter": "prologue",
      "fulfilled_in_chapter": "7",
      "status": "fulfilled"
    }
  ],
  "consistency_notes": "HOV witching hour is 6pm (after which lanes open to all traffic). Location is Crystal City → Pentagon → Tackett's Mill. Driver is in green Acura. These details must stay consistent.",
  "last_updated": "2026-01-10"
}
```

---

### Metaphor Entity
```json
{
  "entity_id": "metaphor-engine",
  "entity_type": "metaphor",
  "name": "The Engine",
  "first_appearance": {
    "chapter": "5",
    "section": "Markets: The Engine of Surplus",
    "context": "Introduced as metaphor for capitalism's role in Ring"
  },
  "definition": "Capitalism as the surplus-generating engine that underwrites all other habitats",
  "attributes": {
    "represents": "Capitalism/markets habitat",
    "key_qualities": [
      "Generates surplus at scale",
      "Powers/funds other habitats",
      "Requires fuel (participation, innovation)",
      "Can overheat/breakdown if misused"
    ],
    "counterpart_metaphors": [
      "The Shell (safety commons)",
      "The Table (family)",
      "The Circle (anarchy)"
    ]
  },
  "appearances": [
    {
      "chapter": "5",
      "section": "Throughout",
      "context": "Established as primary metaphor",
      "reference_type": "full"
    },
    {
      "chapter": "7",
      "section": "Hybrids in the Wild",
      "context": "Engine feeding the shell",
      "reference_type": "brief"
    },
    {
      "chapter": "9",
      "section": "Obligation to Excess",
      "context": "Personal participation in the engine",
      "reference_type": "brief"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "framework-ring",
      "relationship_type": "represents-component",
      "description": "Engine = capitalism habitat in Ring"
    },
    {
      "related_entity_id": "metaphor-shell",
      "relationship_type": "pairs-with",
      "description": "Engine generates resources, Shell protects"
    }
  ],
  "promises": [],
  "consistency_notes": "Always 'the engine' (lowercase except start of sentence). Engine = capitalism/markets. Don't confuse with other mechanical metaphors.",
  "last_updated": "2026-01-10"
}
```

---

### Promise Entity
```json
{
  "entity_id": "promise-ch9-complete-framework",
  "entity_type": "promise",
  "name": "Chapter 9 delivers complete internal framework",
  "first_appearance": {
    "chapter": "8",
    "section": "Closing",
    "context": "Bridge to Ch 9: 'Next: how to BE inside the ring'"
  },
  "definition": "Forward promise that Ch 9 will provide reader's personal operating system",
  "attributes": {
    "promise_type": "structural",
    "specificity": "high",
    "stakes": "high - this is why readers kept reading"
  },
  "appearances": [
    {
      "chapter": "8",
      "section": "Final paragraphs",
      "context": "Promise made",
      "reference_type": "full"
    },
    {
      "chapter": "9",
      "section": "Throughout",
      "context": "Promise fulfilled",
      "reference_type": "full"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "framework-obligation-to-excess",
      "relationship_type": "fulfilled-by",
      "description": "Ch 9 delivers this framework as part of promise"
    },
    {
      "related_entity_id": "framework-jobs-to-be-done",
      "relationship_type": "fulfilled-by",
      "description": "Ch 9 delivers this framework as part of promise"
    }
  ],
  "promises": [
    {
      "promise_text": "Chapter 9 will give you the complete internal framework for operating inside the Ring",
      "made_in_chapter": "8",
      "fulfilled_in_chapter": "9",
      "status": "fulfilled"
    }
  ],
  "consistency_notes": "This is a critical promise. If Ch 9 doesn't deliver complete framework, readers will feel betrayed.",
  "last_updated": "2026-01-10"
}
```

---

## QUALITY CHECKS

### Entity Extraction Quality Checklist

**Before finalizing extraction:**

**Completeness:**
- [ ] All named characters extracted?
- [ ] All frameworks extracted?
- [ ] All recurring examples extracted?
- [ ] All metaphors extracted?
- [ ] All forward promises extracted?

**Accuracy:**
- [ ] Names exactly as they appear in text?
- [ ] Definitions accurate and clear?
- [ ] First appearances correctly identified?
- [ ] All appearances tracked?

**Relationships:**
- [ ] Connections to other entities mapped?
- [ ] Framework hierarchies clear?
- [ ] Example → framework links established?

**Consistency:**
- [ ] No contradictions with existing entities?
- [ ] Naming conventions followed?
- [ ] Attributes complete and accurate?

**Utility:**
- [ ] Will this help Sonnet maintain consistency?
- [ ] Does this enable continuity checking?
- [ ] Is promise tracking actionable?

---

### Common Extraction Errors

**Error 1: Over-Extraction**
❌ Extracting every minor mention
❌ Creating entities for generic references
❌ Tracking non-recurring elements

**Fix:** Only extract entities that recur or create expectations

---

**Error 2: Under-Extraction**
❌ Missing important frameworks
❌ Skipping recurring examples
❌ Forgetting to track promises

**Fix:** Do complete read-through before extracting; flag anything that might recur

---

**Error 3: Inconsistent Naming**
❌ "The Ring" vs "the ring" vs "Ring model"
❌ "Sarah" vs "Sarah (break room character)"

**Fix:** Use exact name as it appears in manuscript; note variations in consistency_notes

---

**Error 4: Missing Relationships**
❌ Extracting entities in isolation
❌ Not mapping framework dependencies
❌ Missing example → framework connections

**Fix:** Always ask "What does this connect to?"

---

**Error 5: Vague Definitions**
❌ "Important concept in the book"
❌ "Character who appears in Chapter 9"

**Fix:** Provide clear, specific, usable definitions

---

## WORKFLOW INTEGRATION

### Where Entity Extraction Happens

**Phase 1 (Foundation Setup):**
- Extract entities from existing manuscript (Chapters 1-8, rough 9-10-Epilogue-Appendix)
- Build initial knowledge graph
- Save as `reference/knowledge-graph/entity-database.json`

**Ongoing (During New Content Creation):**
- Sonnet creates new content
- Opus validates and extracts new entities
- Claude.ai merges into master knowledge graph
- Update `entity-database.json`

**Before Finalization:**
- Complete entity audit
- Verify all promises fulfilled
- Check all relationships
- Ensure consistency across all chapters

---

### File Structure
```
reference/
└── knowledge-graph/
    ├── entity-database.json (master file, all entities)
    ├── framework-library.md (human-readable framework reference)
    ├── character-registry.md (quick character lookup)
    └── promise-tracker.md (promise fulfillment tracking)

editorial/
└── extractions/
    ├── chapter-01-entities.json (per-chapter extractions)
    ├── chapter-02-entities.json
    └── ... (one file per chapter during extraction)
```

**Workflow:**
1. Opus extracts entities from chapter → saves to `editorial/extractions/chapter-XX-entities.json`
2. Claude.ai reviews and approves
3. Entities merged into master `entity-database.json`
4. Human-readable versions generated (`framework-library.md`, etc.)

---

## EXTRACTION EXAMPLES

### Good Extraction Example

**Text from Chapter 5:**
> "The nail-maker's story: 8 nails/day → 10,000 nails/day through specialization. Necessity pile (5,000): covers basics. Surplus pile (4,000): builds security. Excess pile (1,000): free to risk, experiment, give."

**Extracted Entity:**
```json
{
  "entity_id": "example-nail-maker",
  "entity_type": "example",
  "name": "The Nail-Maker",
  "first_appearance": {
    "chapter": "5",
    "section": "The Nail-Maker and the Birth of Excess",
    "context": "Primary example illustrating specialization → surplus → excess mechanism"
  },
  "definition": "Example showing how specialization increases productivity from 8 to 10,000 nails/day, creating necessity (5,000), surplus (4,000), and excess (1,000) piles",
  "attributes": {
    "numbers": {
      "original_production": "8 nails/day",
      "specialized_production": "10,000 nails/day",
      "necessity_pile": "5,000 nails",
      "surplus_pile": "4,000 nails",
      "excess_pile": "1,000 nails"
    },
    "key_insight": "Excess is where sustainable generosity lives",
    "domain": "markets/capitalism"
  },
  "appearances": [
    {
      "chapter": "5",
      "section": "Opening sections",
      "context": "Full development",
      "reference_type": "full"
    },
    {
      "chapter": "9",
      "section": "Obligation to Excess",
      "context": "Referenced as basis for vocation framework",
      "reference_type": "brief"
    }
  ],
  "relationships": [
    {
      "related_entity_id": "framework-obligation-to-excess",
      "relationship_type": "illustrates",
      "description": "Nail-maker example establishes the excess concept"
    },
    {
      "related_entity_id": "framework-ring",
      "relationship_type": "demonstrates-component",
      "description": "Shows how capitalism generates surplus"
    }
  ],
  "promises": [],
  "consistency_notes": "Numbers must stay consistent: 8→10,000, split 5k/4k/1k. These are the canonical figures for this example.",
  "last_updated": "2026-01-10"
}
```

**Why This is Good:**
✅ Specific numbers tracked
✅ Clear definition
✅ Relationships mapped
✅ Consistency note for critical numbers
✅ Appearances tracked

---

### Bad Extraction Example

❌ **Poor extraction:**
```json
{
  "entity_id": "example-1",
  "entity_type": "example",
  "name": "nail thing",
  "first_appearance": {
    "chapter": "5",
    "section": "somewhere in the middle",
    "context": "talks about nails"
  },
  "definition": "An example about making nails",
  "attributes": {},
  "appearances": [],
  "relationships": [],
  "promises": [],
  "consistency_notes": "",
  "last_updated": "2026-01-10"
}
```

**Why This is Bad:**
❌ Vague name ("nail thing")
❌ No specific details
❌ Missing numbers (critical data!)
❌ No relationships
❌ Unusable for continuity checking

---

## HANDOFF TO SONNET

### What Sonnet Needs from Entity Extraction

**When generating new content, Sonnet uses entity database to:**

1. **Check existing entities** before creating new ones
   - "Does Sarah already exist? What do we know about her?"
   
2. **Maintain consistency** across chapters
   - "What was Maya's job title in Ch 10?"
   
3. **Track framework usage** 
   - "Which chapters have already referenced The Ring?"
   
4. **Fulfill promises**
   - "Ch 8 promised we'd deliver X in Ch 9 - did we?"
   
5. **Reuse examples appropriately**
   - "Should I reference slug line here? Has it been established?"

**Sonnet's entity workflow:**
1. Before writing, query entity database for relevant entities
2. During writing, reference entities by exact name
3. After writing, flag any new entities created
4. Self-check: did I contradict any existing entity data?

---

## FINAL QUALITY STANDARDS

### An Excellent Entity Extraction:

✅ **Complete:** All important entities captured  
✅ **Accurate:** Details match manuscript exactly  
✅ **Connected:** Relationships mapped  
✅ **Consistent:** No contradictions  
✅ **Useful:** Enables continuity checking and promise tracking  
✅ **Clear:** Definitions are specific and actionable  
✅ **Maintained:** Updated as manuscript evolves  

**This enables:**
- Seamless continuity across 10+ chapters
- Zero entity contradictions
- All promises tracked and fulfilled
- Frameworks applied consistently
- Examples reused strategically
- Characters behaving consistently
- Reader trust maintained

---

**Entity extraction is the foundation of manuscript quality control. Do it right, and everything else gets easier.**