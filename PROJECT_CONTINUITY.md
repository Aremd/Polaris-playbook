# **Polaris Playbook – Project Continuity (v5)**

---
## **I. Stabilized Acquisitions**
### **Technical Decisions**
| **Element**               | **Details**                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| **Languages/Tools**       | Markdown (docs), Python 3.10+ (scripts), Git/GitHub (versioning), GitHub Actions (CI). |
| **Repository Structure**  | `/core`, `/extensions`, `/templates`, `/scripts`, `/docs`.                |
| **Validation**            | PR + CI (markdownlint, pytest, backward compatibility checks).               |
| **ADRs**                 | MADR format, stored in `/docs/adr/`, linked to PRs/commits.                |
| **Templates**            | Standardized Markdown, validated via `/scripts/validate_templates.py`.    |
| **CI/CD**                | GitHub Actions: linting, testing, and deployment pipelines.                |

### **Local Conventions**
- **Naming**:
  - Files: `kebab-case` (e.g., `project-continuity.md`).
  - Code: `snake_case` (Python) or `camelCase` (JS/TS).
- **Branching**:
  - `main`: Stable.
  - `release/v5.x`: Minor release prep.
  - `feature/*`/`fix/*`: Short-lived (max 2 weeks).
- **Documentation**:
  - All changes must update `/docs/` or inline comments.
  - ADRs required for architectural decisions.

---
## **II. Open Hypotheses (v5)**
| **Topic**               | **Questions**                                  | **Next Steps**                     |
|--------------------------|-----------------------------------------------|------------------------------------|
| **LLM Integration**      | How to generate ADRs/reports via structured prompts? | POC (issue #87).                   |
| **Dynamic Templates**    | Can Jinja2 be used for template customization? | Technical evaluation.             |
| **CI Performance**       | Reduce pipeline execution time (<10s).       | Optimize Python scripts.          |
| **Tool Compatibility**   | Ensure interoperability with Notion/Azure DevOps. | Develop generic connectors.       |

---
## **III. Past Decisions**
### **Architectural Choices**
- **Core/Extensions Separation**: Immutable core + adaptable extensions (v4.0).
- **ADR Process**: MADR format for all major decisions (v3.2).
- **Template Validation**: Automated checks via `/scripts/validate_templates.py` (v5.0).

### **Rejected Approaches**
| **Approach**               | **Reason for Rejection**                     | **Lesson**                          |
|----------------------------|-----------------------------------------------|-------------------------------------|
| Direct core modifications  | Broke backward compatibility.               | Always use ADRs for core changes.   |
| Undocumented template changes | Led to inconsistencies.                   | Link templates to issues/ADRs.     |
| Long-lived branches        | Caused merge conflicts.                      | Enforce 2-week branch lifetime.     |

---
## **IV. Local Working Rules**
### **How to Work Here**
1. **Entry Points**:
   - Start with [`LLM_START_HERE.md`](LLM_START_HERE.md).
   - Check `/docs/adr/` for past decisions.
2. **Sources of Truth**:
   - **Core**: `/core/` + ADRs.
   - **Templates**: `/templates/` + validation scripts.
   - **Scripts**: `/scripts/` + `pytest`.
3. **Validation**:
   - PRs require:
     - Linked issue/ADR.
     - CI passing (linting, backward compatibility, tests).
     - Peer review for core/templates.

---
## **V. Restart Points (v5)**
### **Where to Resume**
- **Priority Task**:
  - Finalize LLM integration (issue #87):
    - Validate POC with Mistral AI.
    - Document in `/docs/llm-integration.md`.
- **Immediate Checks**:
  - Open PRs (especially #92 for Notion compatibility).
  - Backward compatibility tests (`/tests/backward-compatibility/`).

---
## **VI. Past Errors & Lessons**
| **Error**                     | **Impact**                     | **Solution**                          |
|--------------------------------|---------------------------------|---------------------------------------|
| Core changes without ADR      | Broke 3 dependent projects.     | Mandate ADRs for core modifications.  |
| Outdated documentation         | 2 days lost debugging.          | Link docs to code via CI checks.      |
| Long-lived branches           | Merge conflicts.                | Enforce 2-week branch lifetime.      |

---
## **VII. Next Relevant Work (v5)**
1. **LLM Integration**:
   - Generate ADRs/reports via structured prompts.
2. **Template Dynamization**:
   - Evaluate Jinja2 for customizable templates.
3. **CI Optimization**:
   - Reduce pipeline time to <10s.
4. **v5.1 Preparation**:
   - Retrospective + roadmap (focus on `enhancement` issues).

---
## **VIII. Purpose of This Document**
- **Avoid Rediscovery**: Preserve project history and decisions.
- **Enable Handover**: Allow any LLM or new contributor to resume work cleanly.
- **Reduce Methodological Regressions**: Ensure consistency with past choices.

**Use this file to:**
✅ Understand the current state of the project.
✅ Identify open questions and priorities.
✅ Avoid repeating past mistakes.
