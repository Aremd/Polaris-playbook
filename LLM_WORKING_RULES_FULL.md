# **LLM Working Rules — Full**

---

## **Purpose**
Produce changes that are:
- **Functionally correct.**
- **Right in rendering and intention.**
- **Structurally clean.**
- **Maintainable and easy to explain.**
- **Elegant in solution design.**
- **Evolvable over time.**

*A solution that "works" but degrades the codebase, introduces avoidable complexity, or weakens the delivery chain is **not acceptable**.*

---

## **Core Operating Principle**
**Do not execute on the apparent simplicity of a request.**

1. **Classify the task correctly.**
2. **Choose the right mode of work.**
3. **Implement the smallest clean intervention.**
4. **Validate it with the smallest credible safety net.**
5. **Qualify its place in the delivery chain (if relevant).**

---

## **Mandatory Qualification Filter**
Before any change, answer:

### **1. Real Object of Change**
What is **actually** being changed?
- Content
- Local style
- Component
- Template
- Rendering logic
- Routing
- Configuration
- Asset pipeline
- Branding integration
- Generation script
- Workflow/CI/deploy logic
- Metadata/social sharing
- Other: _________

### **2. Systems Touched**
- **One isolated system**?
- **Multiple interacting systems**?
  *(Example: Theme + branding, template + CSS, content + metadata.)*

### **3. Entry Point Certainty**
Is the intended entry point:
- **Proven** (confirmed by prior use or documentation)?
- **Only plausible** (hypothesis based on similarity)?

**Do not implement from a plausible entry point as if it were confirmed.**

### **4. Exact System or Similar Case**
Is this the **exact mechanism** in use, or only something that **looks familiar**?
**Do not rely on neighboring patterns or prior resemblance.**

### **5. Stop/Requalification Threshold**
What **concrete signal** will trigger a stop and reclassification?
*(Example: The second correction does not improve the result.)*

### **6. Success Criteria**
What does success mean **across**:
- **Function** (does it work?)?
- **Rendering** (is it correct and faithful to intent?)?
- **Architecture** (is it at the right level?)?
- **Maintainability** (can others understand/modify it later?)?
- **Elegance** (is it proportionate and sober?)?
- **Evolvability** (can it adapt without redesign?)?

### **7. Minimal Validation Requirement**
What is the **smallest runtime-efficient validation layer** for this change?
*(Example: Manual local validation, targeted unit test, smoke test, build validation, etc.)*

**Do not skip validation when regression risk is real.**

---

## **Decision Rule**

### **Execute Directly Only If:**
- One system is touched.
- The entry point is **proven**.
- The change is **local and reversible**.
- Success criteria are **clear**.
- Validation is **straightforward**.
- No hidden delivery-chain implications exist.

### **Map First If:**
- Multiple systems interact.
- The entry point is **only plausible**.
- Branding, templates, theme logic, responsive behavior, generation scripts, metadata, workflows, or external platform behavior are involved.
- Side effects are possible.
- The clean solution is **not yet clear**.

### **Stop and Requalify If:**
- Two iterations do **not improve** the result.
- Technical correctness and visual/intended correctness **diverge**.
- The solution spreads **without a clear center**.
- New fixes compensate for a **weak initial hypothesis**.
- The change becomes **harder to explain** than the original problem.
- Delivery or validation logic becomes **more complex** than the change itself.

---

## **Intervention Method**

### **1. Map the Existing System**
Identify:
- The **real files** in use.
- The **real partials, wrappers, hooks, templates, classes, workflows, and pipelines**.
- The **actual source of truth** for the behavior being changed.

### **2. Identify the Winning Rule**
Find the **correct level of intervention**:
- Content
- Config
- Template
- Style layer
- Component layer
- Asset layer
- Generation layer
- Workflow/delivery layer

**Do not solve a structural problem with decorative overrides.**

### **3. Intervene at One Legitimate Point**
Prefer the **most central, correct entry point**.
A good intervention should feel:
- **Local.**
- **Justified.**
- **Reversible.**
- **Easy to reason about.**

### **4. Centralize Refinements**
Use the project’s **extension layer** instead of modifying core/theme/vendor sources.
Centralize:
- Style refinements in the proper style layer.
- Generation refinements in the existing generator.
- Workflow changes in the actual delivery chain.

### **5. Keep Code Explainable**
Every change should remain:
- Easy to read.
- Easy to justify.
- Easy to modify later.

**Prefer short, explicit blocks over clever or scattered fixes.**

### **6. Keep Scope Tight**
**One problem = one scope = one coherent intervention.**
Avoid patch chains.

### **7. Validate Locally First**
Distinguish between:
- Local behavior.
- Production behavior.
- Cache/platform behavior.
- External service behavior.
- Workflow/build behavior.

### **8. Clean Before Finishing**
Leave **no**:
- Temporary files.
- Backup files.
- Abandoned experiments.
- Dead CSS.
- Redundant special-case logic.
- Orphaned assets.
- Unnecessary workflow branches.

---

## **Success Criteria**
A change is successful **only if**:

| **Criteria**          | **Requirement**                                                                 |
|------------------------|---------------------------------------------------------------------------------|
| **Function**           | The intended behavior works.                                                   |
| **Rendering**          | The result is correct, legible, and faithful to intent.                       |
| **Architecture**       | The solution acts at the right level without creating side systems.            |
| **Maintainability**    | Another contributor can quickly understand, explain, and modify the change.  |
| **Elegance**           | The solution is proportionate and avoids unnecessary complexity.               |
| **Evolvability**       | The solution can adapt later without forcing redesign.                         |
| **Validability**       | The change can be checked through minimal but credible validation.            |
| **Delivery Fit**       | The change is correctly placed in the build/deploy chain.                      |

---

## **Minimal Testing Rule**
For every non-trivial change, determine the **smallest runtime-efficient validation layer** that provides meaningful confidence.

### **Testing Principles**
- **No extra tests** for purely cosmetic, truly local, low-risk changes.
- **Targeted tests** for critical, reusable, or regression-prone behavior.
- **Prefer fast, high-signal tests** over wide but slow coverage.
- **Assess test value** before adding validation for generation, metadata, or external integration changes.

---

## **Delivery-Chain Qualification**
For any non-trivial change, determine if the impact is **local** or extends into the **delivery chain**.

### **Questions to Answer**
1. Is the change **local**, or does it affect build, artifact generation, deployment, or live-served behavior?
2. Is **scope detection** needed before broader validation?
3. What is the **smallest staged validation chain** that provides meaningful confidence?
   *(Source validation → build validation → artifact validation → pre-deploy smoke test → post-deploy live smoke test.)*
4. What **artifacts** are produced, transformed, or shipped by this change?
5. Does this change touch **workflow/tooling areas** that require CI/CD maintenance checks?

**Do not route every change through the same heavy validation path.**

---

## **Artifact Awareness Rule**
If a change touches **generation, build, export, or deploy packaging**, identify:
- What artifact is **produced**?
- What artifact is **intermediate**?
- What artifact is the **actual deliverable**?
- What **consumes each artifact downstream**?

**Do not modify a generation or delivery chain without understanding what is being produced and why.**

---

## **CI/CD Maintenance Awareness Rule**
If a task touches **workflows, actions, runners, deployment logic, or build tooling**, assess:
- Deprecated actions or runtimes.
- Fragile workflow branching.
- Unnecessary artifact handoffs.
- Redundant stages.
- Validation stages that are too weak or too heavy for the risk level.

*A delivery chain that passes while silently aging into breakage is **not healthy**.*

---

## **Forbidden Mistakes**
Do **not**:
- Implement before minimal mapping.
- Classify by surface simplicity instead of real dependencies.
- Rely on a similar case instead of the exact mechanism in use.
- Stack overrides to save a weak hypothesis.
- Confuse "it displays" with "it is successful."
- Sacrifice code cleanliness for short-term speed.
- Create a second system when an existing coherent pipeline already exists.
- Judge a local change through production/platform behavior alone.
- Leave failed experiments in the repo.
- Add tests mechanically without assessing runtime cost and signal value.
- Send every change through the same delivery path without scope qualification.
- Ignore workflow/tooling debt when touching CI/CD areas.

---

## **Required Response Format Before Acting**
For each task, provide:

### **1. Qualification**
- Real object of change.
- Systems touched.
- Entry point: proven or plausible.
- Exact system or similar case.
- Stop/requalification threshold.
- Success criteria.
- Minimal validation/testing/delivery level.

### **2. Intervention Plan**
- Where you will act.
- Why this is the right entry point.
- What you will **not** touch.
- How you will validate.

### **3. Implementation**
- Minimal patch.
- Centralized scope.
- No drift.
- No opportunistic side changes.

### **4. Validation**
- What was checked.
- What remains uncertain.
- What was intentionally left untouched.
- Any residual doubt stated explicitly.

---

## **What the User Should Demand in Return**
The user should require that the LLM:
1. Qualifies the task before acting.
2. Names the exact intended entry point.
3. Distinguishes proof from hypothesis.
4. States a stop/requalification threshold.
5. Defines success beyond mere functionality.
6. Explains why the proposed solution is the cleanest sufficient one.
7. Avoids opening a parallel system without strong justification.
8. Proposes the smallest credible validation layer.
9. Keeps validation runtime cost proportionate.
10. Identifies delivery-chain implications (if relevant).
11. Proposes the smallest relevant staged validation sequence.
12. Flags avoidable CI/CD tooling debt when workflows/actions are in scope.
13. Leaves the repo clean.
14. Knows when to stop instead of forcing a bad direction.

---

## **One-Line Operating Principle**
**Do not act quickly on apparent simplicity.**
First verify whether the request is truly local or a multi-system compatibility problem, then implement the smallest clean solution and protect it with the smallest credible validation layer—and, when relevant, the smallest justified staged delivery-chain validation.
