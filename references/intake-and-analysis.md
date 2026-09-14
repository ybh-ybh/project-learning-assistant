# Intake and Local Project Analysis

Use this procedure for a new course request. The purpose is to collect only the decisions that materially affect the course and to obtain enough local evidence to recommend a lesson count.

For selected lessons or an explicit update to an existing lesson, reuse the existing outline and course metadata. Do not repeat the full intake or project-wide analysis unless the requested target cannot be resolved from the existing course.

## 1. Resolve the local project

Prefer an explicit absolute path from the user. If none is provided and the current working directory is recognizably a project, propose that directory and ask the user to confirm it. A recognizable project normally contains source directories, project documentation, build manifests, package manifests, or version-control metadata.

If the user provides only a remote repository URL, explain that this skill analyzes local files and ask for the downloaded project's local path. Do not browse or clone the remote repository as a substitute.

Confirm that the directory is readable and contains meaningful project documentation or source code before continuing.

## 2. Perform a preliminary read-only survey

Survey the local tree before recommending a lesson count. Start with inexpensive evidence:

- repository-root documentation and contributor or architecture guides;
- build and package manifests;
- top-level directories and module manifests;
- application or library entry points;
- core domain packages;
- tests that reveal intended behavior;
- local Git metadata.

Use targeted file discovery and search. Exclude generated artifacts, dependency caches, build outputs, vendored dependencies, IDE state, and the selected course output directory. Do not run the project during the default architecture-and-source learning workflow.

The preliminary survey is not the full analysis. Its purpose is to identify the project's rough scale, languages, module boundaries, and likely learning path.

## 3. Recommend a lesson count

Recommend one concrete number from 3 through 10 when the user has not specified a count. Explain the recommendation briefly using observed project characteristics.

Use these ranges as guidance, not a rigid formula:

- **3–5 lessons:** a focused, single-purpose project with few modules and one dominant flow;
- **6–8 lessons:** a medium project with multiple meaningful modules, abstractions, or runtime flows;
- **9–10 lessons:** a large or conceptually dense project with several subsystems and important cross-module behavior.

Honor any user-specified lesson count, including a value outside 3–10. The 3–10 range applies only to recommendations. If the requested count cannot reasonably support the confirmed learning goal, explain the tradeoff before proceeding rather than capping or silently changing it.

## 4. Confirm the five inputs

Collect or confirm these values in one concise message whenever possible:

| Input | If absent |
|---|---|
| Local project directory | Propose the recognizable current project; otherwise request a path. |
| Course language | Recommend the user's current communication language. |
| Lesson count | Recommend 3–10 lessons after the preliminary survey. |
| Learning goal | Recommend architecture and core source code, without deployment or execution. |
| Output directory | Recommend `<confirmed-local-project-root>/<project-name>-course`. |

If all values are explicit and consistent, do not ask redundant questions.

## 5. Protect the output directory

Inspect the exact output path before any write.

- If it does not exist, create it directly after the inputs are confirmed.
- If it exists and is empty, it may be used.
- For a new outline or full course, if it exists and is non-empty, report that fact and ask the user to choose a different directory or explicitly choose how new files should be added.
- For selected lessons or an explicit lesson update, treat existing course files as expected. Ask only if the target is ambiguous or the requested write would affect a file the user did not authorize.
- Never overwrite an existing same-name file without a separate explicit decision.
- Never delete or clear the directory to make it usable.

On a continuation turn, the outline created by this workflow is expected output, not an unrelated conflict. Existing course files are also expected during selected-lesson generation or an explicit lesson update. Still protect unrelated files and require a clear target before modifying an existing lesson.

## 6. Record the local source baseline

Capture the baseline before creating course output inside the source repository.

For a Git project, record:

- current branch;
- exact tag or release identifier pointing at the current commit, when available;
- current commit hash;
- whether relevant tracked or untracked local changes existed before course generation.

Read the source origin only from local Git configuration or local project documentation. It is optional metadata, not an analysis source.

For a non-Git project, inspect local manifests, version files, or release documentation. If no reliable version exists, record `version unknown` in the course language. Do not generate an additional local snapshot identifier.

When the worktree is dirty, state that the course includes local modifications. Do not claim that dirty content is identical to the recorded commit. This version and worktree inspection happens once while preparing the outline and must not be repeated after the user confirms it.

## 7. Perform the full local analysis

After the inputs are confirmed, deepen the analysis enough to design the outline:

1. establish the project's problem statement and public surface;
2. identify architectural layers, major modules, and ownership boundaries;
3. find core data structures, protocols, state, or lifecycle concepts;
4. trace representative entry points into the most important mechanisms;
5. identify the component relationships and representative cross-module flows needed for the Mermaid diagrams and confirmed learning goal;
6. use tests and local documentation to validate intended behavior;
7. note documentation/source disagreements and unresolved uncertainties.

Do not force every project into the same architecture. Let the observed local structure determine the course.
