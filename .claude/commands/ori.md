# Optimize Research Implement (ORI) Workflow

**Version:** 1.2
**Purpose:** Autonomous multi-phase workflow with intelligent model selection for researching, validating, and implementing complex software engineering tasks.

---

## User Request

**Task:** {{args}}

---

## Workflow Overview

Execute the following phases sequentially with built-in error handling, validation, and intelligent model selection:

```
PHASE 0: STRATEGY (Opus)
    ↓
PHASE 1: RESEARCH (Dynamic)
    ↓
PHASE 2: VERIFY (Sonnet)
    ↓
PHASE 3: IMPLEMENT (Sonnet/Haiku)
    ↓
PHASE 4: DOCUMENT (Haiku)
```

---

## Model Selection Strategy

| Phase | Model | Rationale |
|-------|-------|-----------|
| **Phase 0: Strategy** | **Opus** | Complex reasoning, strategic planning, research design |
| **Phase 1: Research** | **Dynamic** | Opus for complex/novel, Sonnet for standard |
| **Phase 2: Verify** | **Sonnet** | Balance of speed and accuracy for validation |
| **Phase 3: Implement** | **Sonnet/Haiku** | Sonnet for complex code, Haiku for simple edits |
| **Phase 4: Document** | **Haiku** | Fast, cost-effective for doc updates |

---

## Phase 0: Research Strategy (STRATEGIC PLANNING)

### Objective
Use Opus to analyze the task and create an optimal research strategy.

### Model: **Opus**

### Instructions

**CRITICAL:** Execute Phase 0 using the Task tool with Opus:

```
Use Task tool with:
- subagent_type: "general-purpose"
- model: "opus"
- prompt: [Phase 0 analysis instructions]
```

### Phase 0 Analysis Steps

1. **Analyze User Request**
   - Parse complexity and scope
   - Identify domain and subdomain (code, data, UX, infrastructure, etc.)
   - Determine novelty (established pattern vs. new problem)
   - Assess information availability (well-documented vs. obscure)
   - Calculate clarity score (0-1.0)
   - Detect risk flags (security, privacy, compliance)

2. **Design Research Strategy**
   Create a structured research plan:
   - **Primary questions** to answer (ranked by priority)
   - **Information sources** (official docs, codebase, web, examples)
   - **Search queries** (specific keywords/phrases)
   - **Validation criteria** (how to verify findings)
   - **Success metrics** (what constitutes "enough" research)

3. **Select Optimal Models**
   Determine which model for each phase:

   **Phase 1 Selection:**
   - IF task is complex OR novel OR ambiguous → **Opus**
   - IF task is standard OR well-documented → **Sonnet**

   **Phase 3 Selection:**
   - IF implementation is complex OR architectural → **Sonnet**
   - IF implementation is simple edits/config → **Haiku**

4. **Generate Handoff Packet**
   Create structured context for Phase 1:
   ```json
   {
     "task": "User's original request",
     "domain": "code|data|ux|infrastructure|...",
     "complexity": "low|medium|high",
     "clarity_score": 0.0-1.0,
     "risk_flags": ["security", "privacy", ...],
     "research_strategy": {
       "questions": ["Q1", "Q2", "Q3"],
       "sources": ["docs", "code", "web"],
       "queries": ["query1", "query2"],
       "validation": ["criterion1", "criterion2"]
     },
     "model_recommendations": {
       "phase_1": "opus|sonnet",
       "phase_3": "sonnet|haiku",
       "reasoning": "explanation"
     }
   }
   ```

5. **Output**
   - Display strategy summary
   - Show model recommendations with reasoning
   - Present handoff packet
   - Transition to Phase 1

---

## Phase 1: Deep Research (OBSERVE & ORIENT)

### Objective
Gather comprehensive, accurate information using all available tools and sources.

### Model: **Dynamic** (based on Phase 0 recommendation)

### Instructions

**Execute Phase 1 using the recommended model from Phase 0:**

```
If Phase 0 recommended Opus:
  Use Task tool with model="opus"

If Phase 0 recommended Sonnet:
  Use Task tool with model="sonnet" (or execute directly)
```

### Research Steps

1. **Web Search & Documentation**
   - Search official documentation for the tech stack
   - Find best practices and current recommendations
   - Look for security advisories and known issues
   - Check latest versions and compatibility

2. **Code Examples & Patterns**
   - Search GitHub for similar implementations
   - Review established patterns in the domain
   - Analyze working examples
   - Identify common pitfalls

3. **Codebase Analysis**
   - Examine existing code structure
   - Identify related components
   - Review current patterns and conventions
   - Check for existing implementations

4. **Synthesize Findings**
   - Consolidate information from all sources
   - Identify best approach
   - Note alternative approaches
   - Document assumptions and constraints

5. **Generate Handoff Packet**
   ```json
   {
     "research_findings": {
       "primary_approach": "...",
       "alternatives": ["approach1", "approach2"],
       "libraries": ["lib1", "lib2"],
       "dependencies": ["dep1", "dep2"]
     },
     "best_practices": ["practice1", "practice2"],
     "security_considerations": ["consideration1", "consideration2"],
     "examples": [
       {"source": "url", "summary": "..."}
     ],
     "assumptions": ["assumption1", "assumption2"],
     "risks_identified": ["risk1", "risk2"]
   }
   ```

---

## Phase 2: Verification (DECIDE)

### Objective
Cross-validate research findings and assess security, performance, and feasibility.

### Model: **Sonnet**

### Instructions

**Execute Phase 2 using Sonnet:**

```
Use Task tool with model="sonnet"
```

### Verification Steps

1. **Cross-Validate Findings**
   - Verify approach is current and recommended
   - Check for conflicting information
   - Confirm compatibility with existing stack
   - Validate assumptions from research

2. **Security Review**
   - Check OWASP Top 10 considerations
   - Review authentication/authorization approaches
   - Assess data exposure risks
   - Verify input validation strategies
   - Check dependency vulnerabilities

3. **Performance Assessment**
   - Evaluate scalability implications
   - Check for performance bottlenecks
   - Review caching strategies
   - Assess database query efficiency

4. **Feasibility Check**
   - Confirm required dependencies are available
   - Verify compatibility with current environment
   - Check for breaking changes
   - Assess implementation complexity

5. **Generate Decision**
   ```json
   {
     "verification_status": "approved|needs_revision",
     "approach_confirmed": "primary|alternative_1|alternative_2",
     "security_checks": {
       "passed": ["check1", "check2"],
       "warnings": ["warning1"],
       "blockers": []
     },
     "performance_assessment": {
       "expected_impact": "low|medium|high",
       "optimizations_needed": []
     },
     "implementation_plan": [
       "step1",
       "step2",
       "step3"
     ],
     "rollback_strategy": "..."
   }
   ```

---

## Phase 3: Implementation (ACT)

### Objective
Execute the solution with verified approach, comprehensive error handling, and testing.

### Model: **Sonnet or Haiku** (based on Phase 0 recommendation)

### Instructions

**Execute Phase 3 using the recommended model:**

```
If Phase 0 recommended Sonnet:
  Use Task tool with model="sonnet"

If Phase 0 recommended Haiku:
  Use Task tool with model="haiku"
```

### Implementation Steps

1. **Pre-Implementation Safety**
   - Verify git status (clean working tree)
   - Create feature branch if needed
   - Back up critical files
   - Review implementation plan

2. **Core Implementation**
   - Follow the verified approach from Phase 2
   - Implement step-by-step with validation
   - Add comprehensive error handling
   - Include input validation
   - Add logging/debugging support

3. **Testing**
   - Write unit tests for core functionality
   - Add integration tests if needed
   - Test error cases and edge cases
   - Verify security controls

4. **Error Handling & Recovery**
   - If errors occur:
     - Log the error with context
     - Attempt automatic resolution
     - If can't resolve, rollback changes
     - Document issue for user

5. **Generate Results**
   ```json
   {
     "implementation_status": "completed|partial|failed",
     "files_modified": ["file1", "file2"],
     "tests_added": ["test1", "test2"],
     "errors_encountered": [],
     "rollback_performed": false,
     "next_steps": ["step1", "step2"]
   }
   ```

---

## Phase 4: Documentation (CLOSE LOOP)

### Objective
Update all relevant documentation and create implementation summary.

### Model: **Haiku**

### Instructions

**Execute Phase 4 using Haiku:**

```
Use Task tool with model="haiku"
```

### Documentation Steps

1. **Update README**
   - Add new feature documentation
   - Update setup instructions if needed
   - Add usage examples
   - Update prerequisites

2. **Update CHANGELOG**
   - Add entry with version/date
   - Describe what was added/changed
   - Note any breaking changes
   - Credit relevant contributors

3. **Create Implementation Summary**
   ```markdown
   # Implementation Summary

   ## Task
   [Original user request]

   ## Approach
   [Chosen approach and reasoning]

   ## Changes Made
   - File 1: Description
   - File 2: Description

   ## Testing
   - Tests added: X
   - Coverage: Y%

   ## Security Considerations
   [Any security measures implemented]

   ## Next Steps
   1. Step 1
   2. Step 2
   ```

4. **Code Comments**
   - Add inline documentation
   - Document complex logic
   - Add TODOs if needed

---

## Error Handling & Recovery

### Throughout All Phases

1. **Monitor for Issues**
   - Track errors and warnings
   - Validate assumptions continuously
   - Check for blockers early

2. **Recovery Strategies**
   - Phase 1: Try alternative sources, adjust queries
   - Phase 2: Request additional clarification, adjust approach
   - Phase 3: Rollback changes, try alternative implementation
   - Phase 4: Skip non-critical updates

3. **User Communication**
   - Report progress at each phase
   - Highlight any issues or concerns
   - Request input when stuck
   - Provide clear next steps

---

## Quality Gates

### Between Each Phase

**Phase 0 → Phase 1:**
- Strategy must be complete
- Risk flags identified
- Model selection justified

**Phase 1 → Phase 2:**
- Minimum 2 sources consulted
- Primary approach identified
- Assumptions documented

**Phase 2 → Phase 3:**
- Security review passed
- No critical blockers
- Implementation plan clear

**Phase 3 → Phase 4:**
- Core implementation complete
- Critical tests passing
- No unresolved errors

---

## Execution Instructions

1. **Start with Phase 0**
   - MUST use Opus via Task tool
   - Generate complete handoff packet
   - DO NOT skip this phase

2. **Follow Model Recommendations**
   - Use the models recommended by Phase 0
   - Don't downgrade complex tasks to Haiku
   - Respect the cost/quality trade-offs

3. **Preserve Context**
   - Pass handoff packets between phases
   - Maintain trace of decisions
   - Document assumptions throughout

4. **Validate at Gates**
   - Check quality gates between phases
   - Don't proceed if gates fail
   - Report blockers to user

5. **Communicate Progress**
   - Report at start of each phase
   - Highlight key findings
   - Note any concerns early

---

## Expected Output

At the end of the workflow, provide:

1. **Executive Summary**
   - What was accomplished
   - Key decisions made
   - Any outstanding issues

2. **Technical Details**
   - Files modified
   - Tests added
   - Dependencies added

3. **Documentation**
   - Updated README/CHANGELOG
   - Implementation notes
   - Usage examples

4. **Next Steps**
   - Any remaining work
   - Testing recommendations
   - Deployment considerations

---

## Begin Execution

Start with Phase 0 using Opus to analyze the user's task and design the optimal research and implementation strategy.