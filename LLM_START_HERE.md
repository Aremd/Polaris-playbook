# **Polaris Playbook – LLM Start Here**

## **1. Expected Work Mode**
This repository implements a **structured, traceable, and collaborative** workflow for the **Polaris Playbook**, a framework for standardizing complex project management. Key principles:
- **Discipline**: Every change must be documented, tested, and validated.
- **Clarity**: Tasks must be qualified before action.
- **Maintainability**: Modifications must be clean, backward-compatible, and explainable.
- **Continuity**: The project must be reproducible by any new contributor (human or LLM).

---

## **2. How to Use `SHORT` and `FULL` Rules**
- **[`LLM_WORKING_RULES_SHORT.md`](LLM_WORKING_RULES_SHORT.md)**: Quick reference for immediate tasks (commit structure, PR requirements, priority handling).
- **[`LLM_WORKING_RULES_FULL.md`](LLM_WORKING_RULES_FULL.md)**: Detailed guidelines for deep work (ADR process, testing, documentation standards, architectural decisions).

**Use `SHORT` for quick actions, `FULL` for complex or architectural tasks.**

---

## **3. Local Conventions**
### **Structure Conventions**
- **Directories**:
  - `/core`: Immutable rules and processes.
  - `/extensions`: Optional modules (e.g., risk management).
  - `/templates`: Standardized Markdown files.
  - `/scripts`: Automation and validation scripts (Python).
  - `/docs`: All documentation, including ADRs (Architectural Decision Records).
- **Files**:
  - `kebab-case` for filenames (e.g., `risk-assessment-template.md`).
  - `snake_case` for Python scripts/functions.

### **Design Conventions**
- **Templates**: Must follow the Markdown structure defined in `/templates/README.md`.
- **ADRs**: Use the [MADR format](https://adr.github.io/madr/) and store in `/docs/adr/`.
- **Scripts**: Include docstrings and type hints (Python 3.10+).

### **Build/Deploy Conventions**
- **Versioning**: [Semantic Versioning](https://semver.org/) (`MAJOR.MINOR.PATCH`).
- **Branches**:
  - `main`: Stable, protected.
  - `release/vX.Y`: Preparation for minor releases.
  - `feature/*`/`fix/*`: Short-lived branches (max 2 weeks).
- **CI/CD**: GitHub Actions for linting, testing, and validation (see `.github/workflows/`).

---

## **4. Preferred Entry Points**
| **Layer**          | **Purpose**                          | **Entry Point**                     |
|---------------------|--------------------------------------|-------------------------------------|
| **Core**            | Immutable rules/processes.          | `/core/` + ADR validation.         |
| **Extensions**      | Optional features.                   | `/extensions/` + issue discussion.  |
| **Templates**       | Standardized documents.              | `/templates/` + validation script.  |
| **Scripts**         | Automation/validation.               | `/scripts/` + `pytest`.             |
| **Documentation**   | Guides, ADRs, and tutorials.          | `/docs/` + Markdown linting.        |

---

## **5. No-Go Zones**
- **Direct modifications to `/core`**: Requires an ADR.
- **Undocumented changes**: Every PR must link to an issue or ADR.
- **Long-lived branches**: Max 2 weeks; otherwise, rebase/close.
- **Bypassing CI**: All PRs must pass linting, testing, and validation.

---

## **6. Validation Philosophy**
- **Traceability**: Every change must be linked to an issue, ADR, or PR.
- **Peer Review**: Mandatory for core/templates changes.
- **Automation**: CI must pass (linting, backward compatibility, tests).
- **Documentation**: Code and process changes require doc updates.

**Good work in this repo is:**
✅ **Traceable** (linked to issues/ADRs).
✅ **Tested** (CI passes, manual validation for critical changes).
✅ **Documented** (updates in `/docs/` or inline comments).
✅ **Backward-compatible** (no breaking changes without deprecation warnings).

---

## **7. Recurring Points of Attention**
- **ADR Compliance**: Always check `/docs/adr/` before modifying core/extensions.
- **Template Validation**: Run `/scripts/validate_templates.py` before PRs.
- **CI Performance**: Monitor pipeline execution time (target: <10s).
- **Issue Hygiene**: Prioritize `priority:high` and `good first issue` labels.
