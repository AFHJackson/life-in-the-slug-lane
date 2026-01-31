# PROJECT DECISION LOG
**Purpose:** Record key decisions, rationale, and implications  
**Last Updated:** January 10, 2026

---

## HOW TO USE THIS LOG

**When to Log a Decision:**
- Affects project structure or workflow
- Changes target audience or content strategy
- Alters timeline or approach
- Resolves a significant question
- Establishes a principle or constraint

**Format:**
- **Decision:** What was decided
- **Date:** When
- **Rationale:** Why
- **Implications:** What this affects
- **Status:** Active / Revised / Superseded

---

## DECISIONS LOG

### D001: Use Systems-Engineering Approach to Book Writing
**Date:** January 10, 2026  
**Decision:** Apply software development methodology (entity extraction, knowledge graphs, version control, AI agents) to book creation process.

**Rationale:**
- Joshua thinks in systems/relationships (natural fit)
- Token limits make traditional all-in-context approach unsustainable
- Need consistency enforcement across large manuscript
- AI agents can translate systems → accessible narrative
- Local files + version control enables proper workflow

**Implications:**
- Requires VS Code setup and learning curve
- Depends on entity/relationship extraction quality
- Makes collaboration more technical but more scalable
- Enables multi-agent workflow (Opus + Sonnet specialization)

**Status:** ✅ Active

---

### D002: Target Galvanizing + Tenacity Geniuses (Not I+D)
**Date:** January 10, 2026  
**Decision:** Write specifically for readers with Galvanizing and/or Tenacity Working Geniuses, NOT for fellow Invention/Discernment types.

**Rationale:**
- I+D readers would appreciate but not act
- G readers rally others and organize movements
- T readers drive implementation to completion
- G+T together creates multiplier effect (spread AND complete)
- Joshua's invention needs partners for galvanizing and tenacity

**Implications:**
- Every content decision filtered through "will this work for G+T?"
- Must include rally-ready frameworks and shareable language
- Must show action pathways and completion milestones
- Style must inspire and enable, not just inform
- Success metrics change (not reviews, but movements formed)

**Status:** ✅ Active

**Related Documents:**
- WORKING_GENIUSES_RESEARCH.md
- TARGET_AUDIENCE_PROFILE.md (to be created)
- CONTENT_STRATEGY.md (to be created)

---

### D003: Three-Role Project Structure
**Date:** January 10, 2026  
**Decision:** Divide labor across three distinct roles: Joshua (architect), Claude.ai Project (orchestrator), VS Code Agents (executors).

**Rationale:**
- Joshua best at systems frameworks and novel insights
- Claude.ai Project best at coordination and consistency tracking
- VS Code agents best at content generation and validation
- Clear division prevents role confusion
- Enables parallel work streams

**Implications:**
- Joshua provides frameworks, not prose
- Claude.ai Project coordinates, doesn't write book
- VS Code agents generate content from frameworks
- Handoff protocols become critical
- Success requires clear task definition

**Status:** ✅ Active

---

### D004: Opus for Structure, Sonnet for Content, Opus for Review
**Date:** January 10, 2026  
**Decision:** Use Opus 4.5 for architecture and validation phases, Sonnet 4.5 for content generation, Opus 4.5 for final review.

**Rationale:**
- Opus has deeper reasoning for complex frameworks
- Sonnet has faster, more fluent narrative generation
- Opus better at catching subtle inconsistencies
- Sonnet more efficient for iterative editing
- Playing to each agent's strengths

**Implications:**
- Need clear handoff protocols between agents
- Opus validates before Sonnet writes
- Sonnet generates from validated structure
- Opus reviews after Sonnet completes
- Timeline assumes this workflow

**Status:** ✅ Active

**Dependencies:**
- AGENT_HANDOFFS.md must define transition protocols
- VS Code must support both agents smoothly

---

### D005: Mine Existing Content, Don't Start From Scratch
**Date:** January 10, 2026  
**Decision:** Extract entities/relationships from existing manuscript content, use as knowledge base, selectively migrate strong pieces.

**Rationale:**
- Existing content contains valid insights and examples
- Complete rewrite wastes good material (e.g., slug line story)
- Entity extraction preserves structural knowledge
- Allows targeted improvement rather than wholesale replacement
- Faster than pure greenfield writing

**Implications:**
- Must perform entity extraction on all existing chapters
- Need knowledge graph to organize extracted content
- Some content will migrate, some will be regenerated
- Quality depends on extraction thoroughness
- Existing content becomes reference library, not direct source

**Status:** ✅ Active

**Dependencies:**
- ENTITY_EXTRACTION_GUIDE.md required
- Knowledge graph schema required
- Extraction tools/process defined

---

### D006: Full Comprehensive Package (Not Minimal Starter)
**Date:** January 10, 2026  
**Decision:** Build complete foundation package with all documents, not minimal starter set.

**Rationale:**
- Joshua prefers complete structure upfront
- Missing pieces create gaps that demotivate
- Comprehensive setup prevents "what's next?" paralysis
- Can always iterate, but foundation needs to be solid
- Token limits reset, so we can build it all now

**Implications:**
- More upfront work before execution begins
- Longer setup phase (2-3 sessions)
- Better clarity and fewer disruptions later
- Foundation serves as reference throughout project

**Status:** ✅ Active

---

### D007: Dependency-Ordered Development
**Date:** January 10, 2026  
**Decision:** Build in strict dependency order - foundations before dependent pieces, never skip layers.

**Rationale:**
- Prevents building on unstable foundations
- Reduces rework and backtracking
- Joshua values consistency and structure
- Each layer informs the next
- Systematic approach matches systems-thinking philosophy

**Implications:**
- Setup takes longer initially
- Can't jump ahead to "exciting" parts
- Must complete Phase 0 before Phase 1
- Progress may feel slow early, accelerates later
- Discipline required to follow sequence

**Status:** ✅ Active

---

### D008: Pivot from G+T to I→D→G Voice Architecture
**Date:** January 19, 2026  
**Decision:** Rebuild book targeting D+G readers with I→D→G voice, not G+T readers with action-oriented voice.

**Rationale:**
- Joshua's authentic authority is I+D, not T (cannot prescribe actions outside domain)
- G+T target was pulling book toward prescriptive advice author cannot authoritatively give
- Natural Working Genius flow: I creates → D verifies → G spreads → T implements
- Book should provide diagnostic tools (I+D domain), not implementation prescriptions (T domain)
- D readers test frameworks, G readers spread verified ideas, T readers implement in their contexts
- More authentic, more coherent, still creates impact

**Implications:**
- Complete renovation of audience research (I+D+G vs. G+T)
- Major rebuild of Book DNA Writing Guide (I→D→G voice architecture)
- All 13 chapter outlines revised (Part 3: "Verification & Spread" not "Application")
- Agent prompts completely rewritten (diagnostic + rally-ready, not prescriptive)
- New bake-offs needed (Prologue + Chapter 1 with I→D→G voice)

**Voice Formula:**
- **Draws from I:** Present frameworks as inventions
- **Speaks in D:** Invite verification, acknowledge authority limits
- **Speaks to G:** Provide rally-ready language for spreading

**Status:** ✅ Active (supersedes D002: G+T target)

**Next Steps:**
1. Research I voice patterns
2. Research D reader preferences
3. Research G reader preferences  
4. Build I→D→G voice guide
5. Rebuild chapter outlines
6. Generate new agent prompts
7. Run bake-offs with new architecture

---

## OPEN QUESTIONS (Awaiting Decision)

### Q001: Granularity of Entity Extraction
**Question:** How detailed should entity extraction be? Every concept, or just major frameworks?

**Options:**
- A) Extract everything (exhaustive, slow)
- B) Extract only major concepts/examples (faster, risk missing connections)
- C) Start minimal, add as needed (iterative, may require rework)

**Recommendation:** Option C (start minimal, expand)

**Status:** 🟡 Open - will decide during entity extraction testing

---

### Q002: Existing Content Migration Strategy
**Question:** Which existing content should migrate wholesale vs. be regenerated?

**Factors to Consider:**
- Quality alignment with G+T audience
- Structural fit with new architecture
- Consistency with knowledge graph
- Amount of required editing vs. regeneration cost

**Status:** 🟡 Open - will decide after entity extraction complete

---

### Q003: Knowledge Graph Tool/Format
**Question:** What tool/format for knowledge graph? JSON? Database? Specialized tool?

**Options:**
- A) Simple JSON file (portable, version-controllable)
- B) Graph database (powerful, adds complexity)
- C) Markdown with structured linking (readable, limited functionality)

**Status:** 🟡 Open - will decide during schema design

---

## SUPERSEDED DECISIONS

### D002: Target Galvanizing + Tenacity Geniuses (Not I+D)
**Date:** January 10, 2026  
**Status:** ⛔ SUPERSEDED by D008 (January 19, 2026)

**Original Decision:** Write specifically for readers with Galvanizing and/or Tenacity Working Geniuses, NOT for fellow Invention/Discernment types.

**Why Superseded:** Joshua's authentic authority is I+D, not T. The G+T target was pulling the book toward prescriptive advice the author cannot authoritatively give. D008 pivots to I→D→G voice architecture that aligns with Joshua's actual genius profile.

**See D008 for current approach.**

---

## DECISION PRINCIPLES

**Standing Rules We've Established:**

1. **I→D→G Voice First:** Every content decision filtered through "Does this match I→D→G voice architecture?" (Invention frames, Discernment verifies, Galvanizing spreads)

2. **Dependency Awareness:** Build foundations before dependent pieces, no skipping layers.

3. **Role Clarity:** Joshua architects, Claude.ai orchestrates, VS Code executes. No blurring.

4. **Consistency Over Novelty:** Preserve established entities and relationships; change only when necessary.

5. **Diagnostic Over Prescriptive:** Book provides recognition and diagnostic tools, NOT action prescriptions. T-domain implementation left to T-genius readers.

6. **Evidence-Based:** Track what works, adjust based on results, log the reasoning.

7. **Authority Limits Acknowledged:** Don't claim expertise outside Joshua's I+D domain. Acknowledge what the author can and cannot prescribe.

---

**This log grows throughout the project. Check before making major decisions.**