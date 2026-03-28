# **LLM Working Rules — Short**

---

## **Core Rule**
**Do not act on apparent simplicity.**

1. **Qualify the task first.**
2. **Choose the right mode of work.**
3. **Implement the smallest clean solution.**
4. **Validate it with the smallest credible safety net.**

---

## **Mandatory Qualification Before Acting**
Before any change (code, design, UI, template, workflow, or structural content), answer:

1. **What is the real object of change?**
   *(Content, template, rendering logic, workflow, metadata, etc.)*

2. **What systems are touched?**
   *(Single system? Multiple interacting systems?)*

3. **Is the entry point proven or only plausible?**
   *(Do not implement from a plausible entry point as if it were confirmed.)*

4. **Is this the exact system or only a similar case?**
   *(Do not rely on resemblance; confirm the actual system.)*

5. **What is the stop/requalification threshold?**
   *(Example: Two iterations without clear improvement → stop and requalify.)*

6. **What does success mean here?**
   - Functionally correct?
   - Rendering and intention aligned?
   - Structurally clean?
   - Maintainable and evolvable?
   - Validated at the right level?

7. **What is the smallest credible validation level?**
   *(Manual local validation? Targeted test? Smoke test? Staged delivery validation?)*

**Do not implement before answering these questions.**

---

## **Decision Rule**

### **Act directly only if:**
- One system is touched.
- The entry point is **proven**.
- The change is **local and reversible**.
- Success criteria are **clear**.
- Validation is **straightforward**.

### **Map first if:**
- Multiple systems interact.
- The entry point is **only plausible**.
- Branding, templates, workflows, or platform behavior are involved.
- Side effects are possible.
- The clean solution is **not yet clear**.

### **Stop and requalify if:**
- Two iterations do **not improve** the result.
- Technical success and intended/rendered success **diverge**.
- The solution spreads **without a clear center**.
- New fixes compensate for a **weak initial hypothesis**.
- The solution becomes **harder to explain** than the original problem.

---

## **Intervention Rule**
- **Map the real system** before acting.
- **Identify the real source of truth**.
- **Intervene at one legitimate point**.
- **Prefer central, reversible, explainable changes**.
- **Avoid patch chains** and parallel systems.
- **Keep scope tight**.
- **Validate locally first**.
- **Clean before finishing**.

**One problem = one scope = one coherent intervention.**

---

## **Success Rule**
A solution is successful **only if** it is:
✅ Functionally correct.
✅ Right in rendering and intention.
✅ Structurally clean.
✅ Maintainable and evolvable.
✅ Validated at the right level.
✅ Proportionate to the problem.

*A solution that "works" but degrades the codebase is **not acceptable**.*

---

## **Delivery-Chain Rule**
If the change touches **build, artifacts, deploy, metadata, or generation**:
1. Determine if **scope detection** is needed.
2. Define the **smallest staged validation chain**.
3. Assess **artifact implications**.
4. Check **workflow/tooling maintenance implications**.

**Do not route every change through the same heavy path.**

---

## **Forbidden Mistakes**
Do **not**:
- Implement before minimal mapping.
- Classify by surface simplicity instead of real dependencies.
- Rely on a similar case instead of the exact mechanism.
- Stack overrides to save a weak hypothesis.
- Confuse "it displays" with "it is successful."
- Sacrifice cleanliness for speed.
- Create a second system when a coherent one exists.
- Leave failed experiments in the repo.
- Add tests mechanically without assessing value.

---
