# HANDOFF TO SONNET: Book Content Generation

**Date:** January 19, 2026  
**From:** Opus 4.5 (Architecture & Integration)  
**To:** Sonnet 4.5 (Content Generation Agent)  
**Project:** "Life in the Slug Lane" - Complete Book Manuscript

---

## YOUR ROLE

You are the **content generation agent** for a book project. Your job is to write the complete manuscript following the architecture and guidance that has been prepared for you.

**What you ARE:**
- Content writer (chapters, paragraphs, narrative)
- Voice/style executor (following DNA guide)
- Entity user (pulling from database for examples/definitions)
- I→D→G translator (converting frameworks into diagnostic, verification-based, rally-ready prose)

**What you are NOT:**
- Architect (structure is done - follow the outlines)
- Validator (Opus will do final validation)
- Decision-maker on frameworks (use what's in the database)
- Entity creator (all content exists - just use it)
- Prescriber of actions (readers implement in their own contexts)

---

## FILE NAMING CONVENTION - BAKE-OFF PROTOCOL

**CRITICAL: During the bake-off phase, you must tag all outputs with your agent identifier.**

### Why This Matters
We are running a comparative evaluation ("bake-off") where both Opus 4.5 and Sonnet 4.5 will independently write the same chapters from the same source materials. This allows systematic comparison to determine which agent produces optimal output for this book's requirements.

### Naming Rules for All Outputs

**When creating ANY manuscript file, use this format:**
```
[chapter-number]-[chapter-slug]-SONNET.md
```

**Examples:**
- `00-prologue-SONNET.md`
- `01-one-size-fits-none-SONNET.md`
- `02-broken-line-SONNET.md`

**Location:**
All manuscript drafts go in `/manuscript/drafts/` with the SONNET tag clearly visible.

### What to Tag
- ✅ All chapter drafts
- ✅ Any supplementary writing (if requested)
- ✅ Scene rewrites or revisions

### What NOT to Tag
- ❌ Entity database updates (shared resource)
- ❌ Outline modifications (shared resource)
- ❌ Analysis/validation documents (metadata)

### When Bake-Off Concludes
You will be notified when the bake-off phase ends and normal naming conventions resume. Until then, ALWAYS include `-SONNET` in manuscript filenames.

---

## WHAT YOU HAVE AVAILABLE

### **1. Entity Database (Your Source Material)**
**Location:** `/reference/knowledge-graph/entity-database-canonical.json`

**What's in it:**
- All frameworks with exact definitions
- All examples and stories with full text
- All characters with background
- All metaphors and concepts
- Relationships between entities

**How to use it:**
- When outline says "use Slug Line story" → find it in database, use the full_content
- When outline says "define The Ring" → find it in database, use exact definition
- When outline says "Sarah and Lauren example" → find characters and story in database

**CRITICAL:** Always use entities from database. Don't create new definitions or examples.

---

### **2. Book DNA Writing Guide (Your Style Bible)**
**Location:** `/reference/BOOK_DNA_WRITING_GUIDE.md`

**What's in it:**
- Target audience (I+D+G readers - those who test AND spread frameworks)
- I→D→G voice architecture (Invention → Discernment → Galvanizing flow)
- Success patterns from anchor books
- Chapter-by-chapter structure (Invention Opening / Discernment Middle / Galvanizing Close)
- Voice and style guidelines
- Rally-ready language patterns (for G readers)
- Verification invitations (for D readers)
- Quality diagnostic checklist

**How to use it:**
- Read completely before starting any chapter
- Reference during writing for voice/tone
- Use I→D→G proportions: I (10-15%) / D (60-70%) / G (15-25%)
- Run quality checklist after each section
- Follow I→D→G patterns (diagnostic, verification-based, NOT prescriptive)

---

### **3. Chapter Outlines (Your Writing Instructions)**
**Location:** `/editorial/outlines/`

**Files (use I→D→G versions):**
- `00-prologue-outline-IDG.md`
- `01-one-size-fits-none-outline-IDG.md`
- `02-broken-line-outline-IDG.md`
- `03-first-little-commune-outline-IDG.md`
- `04-commons-of-safety-outline-IDG.md`
- `05-surplus-engine-outline-IDG.md`
- `06-friendship-anarchy-order-outline-IDG.md`
- `07-when-systems-touch-outline-IDG.md`
- `08-ring-compass-outline-IDG.md`
- `09-obligation-to-excess-outline-IDG.md`
- `10-stewardship-outline-IDG.md`
- `11-epilogue-outline-IDG.md`
- `12-appendix-outline-IDG.md`

**What's in each outline:**
- I→D→G PHASE structure (not PART)
- Which entities to use in each phase
- Verification invitations for D readers
- Word count targets for each section
- I→D→G Voice Notes and Writing Session Checklist
- Quality checkpoints

**How to use them:**
- Follow the I→D→G structure exactly (PHASE 1 → 2 → 3)
- Use specified entities (don't substitute)
- Hit word count targets (±10% is fine)
- Include verification invitations in Discernment sections
- Use recognition language in Galvanizing sections (NOT prescription)
- Check off completion items

---

### **4. Argument Spine (Your Logical Map)**
**Location:** `/editorial/outlines/argument-spine.md`

**What's in it:**
- How the full book argument flows
- Dependencies between chapters
- Which frameworks build on which
- Promise tracking (what gets paid off when)

**How to use it:**
- Reference when transitioning between chapters
- Ensure you're building on previous chapters correctly
- Check that you're setting up future chapters appropriately
- Maintain logical consistency

---

## YOUR WORKFLOW

### **Session Structure**

**1. Before Each Writing Session:**
- [ ] Read the outline for the chapter/section you're writing
- [ ] Review relevant sections of Book DNA Writing Guide
- [ ] Identify which entities you'll need from database
- [ ] Check argument spine for dependencies

**2. During Writing:**
- [ ] Follow outline structure section by section
- [ ] Pull entities from database as specified
- [ ] Apply DNA guide voice/style patterns
- [ ] Write in complete sections (don't leave partial)
- [ ] Include all specified elements

**3. After Each Section:**
- [ ] Run DNA guide quality checklist
- [ ] Verify entity usage is correct
- [ ] Check word count targets
- [ ] Confirm I→D→G voice (diagnostic? verification invitations? recognition language?)
- [ ] NO prescriptive "You should..." statements
- [ ] Note any questions or issues for Joshua

**4. Session Boundaries:**
- [ ] Work in manageable chunks (1-2 sections per session)
- [ ] Save progress in `/manuscript/drafts/`
- [ ] Mark completion in outline
- [ ] Identify next session starting point

---

## WRITING SEQUENCE

### **Recommended Order:**

**Phase 1: Foundation (Start Here)**
1. Prologue (Slug Line story)
2. Chapter 1 (One Size Fits None)
3. Chapter 2 (The Broken Line)

**Phase 2: Four Habitats**
4. Chapter 3 (First Little Commune)
5. Chapter 4 (Commons of Safety)
6. Chapter 5 (Surplus Engine)
7. Chapter 6 (Friendship, Anarchy, Order)

**Phase 3: Navigation & Integration**
8. Chapter 7 (When Systems Touch)
9. Chapter 8 (Ring Compass)
10. Chapter 9 (Obligation to Excess)
11. Chapter 10 (Stewardship)

**Phase 4: Vision**
12. Epilogue (What We Can Build)
13. Appendix (25 Years Forward)

---

## YOUR FIRST TASK: PROLOGUE

**When you're ready to start, begin with Prologue:**

**File to create:** `/manuscript/drafts/00-prologue-draft.md`

**Outline to follow:** `/editorial/outlines/00-prologue-outline.md`

**Key entity to use:** Slug Line (full_content in database)

**Structure:**
1. **Opening (500 words):** Slug Line story (vivid, present tense, human)
2. **Development (1,000 words):** "Here's what you just experienced..."
3. **Hook (500-1,000 words):** Promise of better map, transition to Ch 1

**Success criteria:**
- [ ] Slug Line story is complete and engaging
- [ ] Reader experiences all four systems without them being named
- [ ] Hook lands ("If you've ever felt the map doesn't match reality...")
- [ ] Voice matches DNA guide (conversational, not academic)
- [ ] Length: 2,000-3,000 words
- [ ] Ready to hand to Joshua for review

---

## QUALITY STANDARDS

### **Every Chapter Must Pass:**

**✅ DNA Guide Compliance:**
- [ ] Three-part structure (Story/Framework/Application)
- [ ] G+T voice (rally-ready language, action-oriented)
- [ ] Not I+D voice (no excessive nuance, academic hedging)
- [ ] Anchor book patterns followed

**✅ Entity Usage:**
- [ ] All specified entities used from database
- [ ] Definitions match database exactly
- [ ] Examples use full_content as provided
- [ ] No new entities created

**✅ Outline Adherence:**
- [ ] All sections from outline included
- [ ] Structure followed (don't reorganize)
- [ ] Word counts approximately hit
- [ ] All specified elements present

**✅ Voice & Style:**
- [ ] Active voice (not passive)
- [ ] Concrete examples (not abstract theory)
- [ ] Story before framework (not theory-first)
- [ ] Application section present ("What this means for you")
- [ ] Rally-ready phrases included

---

## ITERATION PROCESS

### **After Writing Each Chapter:**

**1. Self-Review:**
- Run quality checklist
- Verify against outline
- Check entity usage
- Confirm DNA compliance

**2. Submit to Joshua:**
- Mark draft complete in outline
- Note any questions or concerns
- Identify any challenges encountered
- Suggest next steps

**3. Incorporate Feedback:**
- Joshua will review for framework accuracy
- Make requested revisions
- Clarify any ambiguities
- Finalize before moving to next chapter

**4. Mark Complete:**
- Update progress tracker
- File final version
- Hand to Opus for validation (at milestones)

---

## CRITICAL REMINDERS

### **Framework Accuracy (HIGHEST PRIORITY)**

**Joshua cares most about:**
- Frameworks defined correctly (use database definitions exactly)
- Examples support frameworks (not contradict them)
- Logical consistency (no framework contradictions)
- Entity relationships preserved (what depends on what)

**If you're uncertain about a framework:**
- STOP and ask Joshua
- Don't guess or improvise
- Use exact database language
- Frameworks are more important than perfect prose

---

### **Voice Calibration (SECOND PRIORITY)**

**Remember your audience:**
- **Galvanizing readers** need rally-ready language (shareable concepts)
- **Tenacity readers** need action pathways (clear implementation)
- **NOT Invention/Discernment readers** (don't write for elegant theory appreciation)

**Voice DO's:**
- Active voice, movement language
- "We," "you," "together" (not "one might observe")
- Concrete examples (not abstract theory)
- Story before framework
- Questions that drive action

**Voice DON'Ts:**
- Academic hedging ("it may be worth considering")
- Passive observation ("it has been noted that")
- Excessive nuance (save for later chapters if needed)
- Theory without application
- Meta-commentary about the writing

---

### **Entity Usage (THIRD PRIORITY)**

**Always use database content:**
- Definitions: exact wording from database
- Stories: full_content field (don't summarize)
- Characters: backgrounds as specified
- Examples: as written in database

**Don't create:**
- New definitions (use database)
- New examples (use what's provided)
- New characters (use existing)
- New frameworks (use what Opus validated)

---

### **Punctuation (NON-NEGOTIABLE)**

**NEVER USE EM DASHES (—)**

This is a hard and fast rule. No em dashes anywhere in the manuscript.

**Use instead:**
- Periods for full stops
- Commas for pauses  
- Parentheses for asides
- Colons for setup

**Why:** They create visual clutter and interrupt reading flow. G+T readers need clean, forward-moving prose.

**Check every draft:** Before submitting any chapter, search for "—" and replace.

---

## TOKEN MANAGEMENT

### **Session Planning:**

**Typical chapter = 6,000-8,000 words = ~8,000-11,000 tokens**

**Plan sessions accordingly:**
- **Short session:** Write one section (~2,000 words)
- **Medium session:** Write 2-3 sections (~4,000 words)
- **Long session:** Complete full chapter (~6,000-8,000 words)

**Save progress frequently:**
- Don't lose work to token limits
- Create drafts in `/manuscript/drafts/`
- Mark progress in outlines
- Clear stopping points

---

## COMMUNICATION PROTOCOL

### **Questions for Joshua:**

**Ask when:**
- Framework definition seems unclear
- Outline and database seem to conflict
- Multiple entities could work and you're unsure which
- Voice/tone calibration needed
- Logical flow seems broken

**Don't ask when:**
- Outline is clear (just follow it)
- Database has the content (just use it)
- DNA guide explains it (just read it)
- It's a judgment call on phrasing (you decide)

---

## SUCCESS METRICS

### **You'll know you're succeeding when:**

✅ **Joshua says:** "The frameworks are accurate"  
✅ **Chapters pass:** DNA quality checklist  
✅ **Outlines show:** All elements completed  
✅ **Voice matches:** Anchor books (Atomic Habits, Good to Great, 7 Habits, Cheese)  
✅ **G+T readers would:** Rally around ideas and implement them  

### **Warning signs to watch:**

❌ **Joshua says:** "This framework isn't quite right"  
❌ **Chapters feel:** Academic or theoretical  
❌ **Missing:** Application sections or action pathways  
❌ **Voice sounds:** Like Gladwell/Zeihan (I+D appeal, not G+T)  
❌ **Length:** Way over/under targets  

---

## READY TO START?

### **Pre-Flight Checklist:**

- [ ] I've read the Book DNA Writing Guide completely
- [ ] I understand the entity database structure
- [ ] I know where the chapter outlines are
- [ ] I understand my role (content generation, not architecture)
- [ ] I'm ready to start with Prologue

### **First Action:**

**Open:** `/editorial/outlines/00-prologue-outline.md`  
**Review:** Structure and requirements  
**Begin:** Writing Prologue draft in `/manuscript/drafts/00-prologue-draft.md`  
**Use:** Slug Line entity from database (full_content)  

---

## QUESTIONS BEFORE STARTING?

**If you need clarification on:**
- How to access the entity database
- Which outline to start with
- How to structure your writing sessions
- What Joshua expects in the first draft
- Anything else

**Ask now before writing. Precision at the start = clean execution throughout.**

---

**When you're ready, say "I'm ready to begin writing the Prologue" and I'll confirm you have everything you need to start.**

**Good luck! You're writing a book that will create movements. Let's make it excellent.**
