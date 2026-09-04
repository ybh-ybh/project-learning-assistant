---
name: project-learning-assistant
description: Turn a locally available open-source codebase into a source-grounded, progressive Markdown course with an outline approval gate and verified core-code walkthroughs. Use when a user wants to study a local repository, understand its architecture and core source code, or generate a structured learning course from it. Do not use when only a remote repository URL is available or for general-purpose code documentation.
metadata:
  short-description: Build verified courses from local source code
---

# Project Learning Assistant

Create a progressive course from the actual files in a local open-source project. The default learning goal is to understand the architecture and core source code without deploying or running the project.

## Non-negotiable boundaries

- Analyze a readable local project directory. A remote repository URL may identify the project, but it is never a substitute for the local files.
- Ground project-specific claims in local documentation or source code. Do not fill gaps with assumptions about how similar projects usually work.
- Never overwrite, delete, or clear user files.
- Generate the outline first and end the turn for user confirmation. Do not generate lesson files before the user explicitly confirms that outline.
- Write the course in the confirmed course language. Keep the skill's own instructions and supporting files in English.
- Do not require deployment, execution, or environment setup unless the confirmed learning goal requires it and the user authorizes it.
- Mermaid architecture and call-flow diagrams are not part of this version. Generate them only if the user explicitly expands the request.

## Route the request by phase

Determine which phase the current request is in before acting.

1. **New course:** Resolve the local project and preferences, inspect the project, create only the outline, then request confirmation.
2. **Outline revision:** Apply the user's feedback to the outline, report the revision, and request confirmation again. Do not create lessons.
3. **Confirmed outline:** Mark the outline confirmed, generate every lesson, validate the course, and report the files.

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

If no local project can be identified, ask for its path and stop. If the selected output directory already exists and is non-empty, explain the conflict and ask the user how to proceed before writing anything.

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

Write only `00_<localized-outline-title>.md`. Set its outline status to awaiting confirmation. Then report its path and a concise course summary, ask the user to confirm or request changes, and end the turn.

Do not create placeholder lesson files.

## Phase 3: Generate lessons after confirmation

Treat confirmation as valid only when it clearly refers to the latest outline content.

Before writing lessons:

1. reread the confirmed outline;
2. mark the outline confirmed without requiring another confirmation.

Do not repeat the preliminary survey, full-project analysis, version check, or worktree check after outline confirmation. Read only the source files needed to author and verify each lesson.

Generate exactly one Markdown file for every lesson in the confirmed outline. Use continuous two-digit numbering starting at `01`, followed by a localized lesson title. Follow the lesson contract in [references/course-authoring.md](references/course-authoring.md).

Every lesson must:

- start with the lesson title and then its learning objectives;
- explain the concepts and mechanisms rather than merely list files;
- provide a source-reading route with real project-relative paths and relevant symbols;
- distinguish verified facts from interpretation and unknowns;
- discuss meaningful design decisions or tradeoffs when the evidence supports them;
- end with reflection questions as its final major section.

## Validate before reporting completion

Read and apply [references/validation.md](references/validation.md) before finalizing either the outline or the complete course.

For the complete course, verify at minimum:

- one outline plus exactly the confirmed number of lessons;
- continuous, unique numbering and safe filenames;
- alignment between outline topics and lesson files;
- the confirmed course language and learning goal;
- accurate local version and worktree information recorded in the outline;
- existence of cited files, directories, important code symbols, and evidence for important call or data-flow edges;
- learning objectives first and reflection questions last in every lesson;
- no overwritten, deleted, or cleared user files.

Report the output directory, outline path, lesson file list, source version, and validation performed. State any unverified or uncertain detail explicitly.
