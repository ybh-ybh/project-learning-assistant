---
name: project-learning-assistant
description: Turn a locally available open-source codebase into a source-grounded, progressive Markdown course with an outline approval gate, verified Mermaid architecture and call-flow diagrams, and core-code walkthroughs. Use when a user wants to study a local repository, understand its architecture and core source code, or generate a structured learning course from it. Do not use when only a remote repository URL is available or for general-purpose code documentation.
metadata:
  short-description: Build verified courses from local source code
---

# Project Learning Assistant

Create a progressive course from the actual files in a local open-source project. The default learning goal is to understand the architecture and core source code without deploying or running the project.

## Non-negotiable boundaries

- Analyze a readable local project directory. A remote repository URL may identify the project, but it is never a substitute for the local files.
- Ground project-specific claims in local documentation or source code. Do not fill gaps with assumptions about how similar projects usually work.
- Never overwrite, delete, or clear user files.
- Require a confirmed outline before generating lessons. For a new full or selected-lesson course, create the outline first and end the turn for confirmation. In outline-only mode, create the outline and stop without requesting lesson-generation approval.
- Write the course in the confirmed course language. Keep the skill's own instructions and supporting files in English.
- Do not require deployment, execution, or environment setup unless the confirmed learning goal requires it and the user authorizes it.
- Recommend 3–10 lessons only when the user has not specified a count. Never cap or reject an explicit lesson count merely because it falls outside that range.
- Include a Mermaid architecture or component-relationship diagram in the outline and Mermaid call-flow diagrams in lessons that explain representative core flows.
- Ground every project-specific Mermaid node and edge in the same local evidence required for the surrounding prose.
- Use diagrams to support explanation. They never replace mechanism explanations or source-reading routes.

## Choose the requested output mode

Support four modes:

1. **Full course:** Create and confirm an outline, then generate every lesson.
2. **Outline only:** Create the outline and stop without requesting approval for lesson generation.
3. **Selected lessons:** Generate only the lesson numbers or titles explicitly requested from an existing confirmed outline. If no outline exists, create it and obtain confirmation first.
4. **Update existing lesson:** Edit only the requested lesson. Reuse the existing outline and course metadata; do not regenerate the course or repeat the full intake. Update the outline and request confirmation only when the requested edit changes the lesson title, order, scope, or overall course structure.

An explicit request to update an existing lesson authorizes writing that target file, but never authorizes changes to unrelated files.

## Route the request by phase

Determine which phase the current request is in before acting.

1. **New course:** Resolve the local project and preferences, inspect the project, and create only the outline. Request confirmation unless the user asked for outline-only output.
2. **Outline revision:** Apply the user's feedback to the outline, report the revision, and request confirmation again. Do not create lessons.
3. **Confirmed outline:** Mark the outline confirmed, generate the full course or only the selected lessons, validate the requested output, and report the files.
4. **Existing lesson update:** Read the outline, target lesson, and only the relevant source files; apply and validate the requested update without regenerating unrelated content.

An instruction such as "generate the entire course" given before the outline exists does not waive the confirmation gate. Confirmation must refer to the generated or revised outline.

## Phase 1: Resolve inputs and inspect the project

Read [references/intake-and-analysis.md](references/intake-and-analysis.md) for the complete intake and local-analysis procedure.

Resolve and confirm these five inputs:

- local project directory;
- course language;
- lesson count;
- learning goal;
- output directory.

Ask for missing or uncertain choices together whenever possible. Infer nothing risky. When a value is absent, recommend:

- the user's current communication language for the course language;
- 3–10 lessons based on a preliminary survey of project size and complexity;
- understanding the architecture and core source code, without deployment or execution, as the learning goal;
- `<confirmed-local-project-root>/<project-name>-course` as the output directory.

If no local project can be identified, ask for its path and stop. Create a missing confirmed output directory directly. For a new outline or full course, if the selected output directory already exists and is non-empty, explain the conflict and ask how to proceed before writing. For selected-lesson generation or an explicit existing-lesson update, existing course files are expected; protect unrelated files and ask only when the target is ambiguous or the requested write would conflict with a different file.

Capture the source version and worktree state once while analyzing the project for the outline. Course-generated files must not make a previously clean source tree appear dirty in the recorded baseline.

## Phase 2: Create and confirm the outline

Before authoring, read [references/course-authoring.md](references/course-authoring.md). Use its outline contract and naming rules.

Build the learning sequence from the project's actual architecture and the confirmed learning goal. Cover the knowledge necessary to understand the project, but do not attempt a file-by-file catalog. Prefer this progression when it fits the project:

1. purpose and mental model;
2. architecture and module boundaries;
3. core concepts, data models, and foundational mechanisms;
4. key modules and core source code;
5. cross-module flows and design tradeoffs;
6. end-to-end synthesis.

Write only the uniformly numbered localized outline file, normally `00_<localized-outline-title>.md`. Set its outline status to awaiting confirmation. Report its path and a concise course summary. For a new full or selected-lesson course, ask the user to confirm or request changes and end the turn.

Include at least one Mermaid diagram of the project's overall architecture or component relationships. Build it from the observed local project structure and explain it in the surrounding prose.

Do not create placeholder lesson files.

In outline-only mode, stop after reporting the completed outline. Do not ask the user to approve lesson generation unless they later request lessons.

## Phase 3: Generate lessons after confirmation

Treat confirmation as valid only when it clearly refers to the latest outline content.

Before writing lessons:

1. reread the confirmed outline;
2. mark the outline confirmed without requiring another confirmation.

Do not repeat the preliminary survey, full-project analysis, version check, or worktree check after outline confirmation. Read only the source files needed to author and verify each lesson.

In full-course mode, generate exactly one Markdown file for every lesson in the confirmed outline. In selected-lessons mode, generate exactly the requested lesson files and leave every other lesson untouched. Use the outline's continuous, uniform-width numbering with at least two digits and localized titles. Follow the lesson contract in [references/course-authoring.md](references/course-authoring.md).

Every lesson must:

- start with the lesson title and then its learning objectives;
- explain the concepts and mechanisms rather than merely list files;
- provide a source-reading route with real project-relative paths and relevant symbols;
- include a Mermaid call-flow diagram when the lesson explains a representative core source flow;
- distinguish verified facts from interpretation and unknowns;
- discuss meaningful design decisions or tradeoffs when the evidence supports them;
- end with reflection questions as its final major section.

## Validate before reporting completion

Read and apply [references/validation.md](references/validation.md) before finalizing either the outline or the complete course.

Validate according to the selected output mode. Verify at minimum:

- for a full course, one outline plus exactly the confirmed number of lessons;
- for selected lessons, exactly the requested lesson files without requiring unrequested lessons to exist;
- for an existing-lesson update, only the requested lesson and any explicitly authorized outline change were modified;
- for a full course, continuous and unique numbering; for selected lessons or an update, the requested files retain their outline numbers; all filenames are safe;
- alignment between outline topics and lesson files;
- the confirmed course language and learning goal;
- accurate local version and worktree information recorded in the outline;
- existence of cited files, directories, important code symbols, and evidence for important call or data-flow edges;
- an evidence-grounded Mermaid architecture or component diagram in the outline and Mermaid call-flow diagrams in the relevant lessons;
- learning objectives first and reflection questions last in every lesson;
- no overwritten, deleted, or cleared user files.

Report the output mode, output directory, outline path, created or updated lesson files, source version, and validation performed. State any unverified or uncertain detail explicitly.
