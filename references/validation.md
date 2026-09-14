# Course Validation

Validate observable properties and source accuracy. Do not judge quality only by the presence of expected headings.

## Before writing the outline

- The local project directory is confirmed and readable.
- The course language, lesson count, learning goal, and output directory are confirmed.
- The lesson-count recommendation is based on an actual preliminary survey.
- The output directory is new or empty, or the user has resolved a non-empty-directory conflict.
- No same-name user file will be overwritten.
- The source version and worktree state were captured before course output affected local Git status.

## Before presenting the outline

- The filename begins with `00` and contains a localized outline title.
- The header records the local path, version, worktree state, course language, learning goal, and awaiting-confirmation status.
- Every proposed lesson has a unique number, title, core question, and meaningful project coverage.
- The sequence is progressive and later lessons build on concepts introduced earlier.
- The plan covers the architecture, core mechanisms, important source entry points, and an end-to-end synthesis appropriate to the learning goal.
- The outline contains a Mermaid architecture or component-relationship diagram whose project-specific nodes and edges are supported by local evidence.
- The diagram is explained in prose and does not replace the architecture explanation or source entry points.
- Referenced local documents and source paths exist.
- No lesson files or placeholders were created.

After these checks, report the outline. Stop for explicit confirmation before lesson generation; in outline-only mode, report completion without requesting lesson-generation approval.

## Before generating lessons

- The latest outline content was explicitly confirmed by the user.
- The outline has been reread from disk.
- Existing output files were checked again to prevent overwrites.
- The project survey, full-project analysis, version inspection, and worktree inspection were not repeated after confirmation.

## Validate every lesson

- Its number and title match the confirmed outline.
- The title is followed by learning objectives as the first major section.
- Explanations establish the mechanism before the detailed source route.
- The source walkthrough uses real project-relative paths and verified important symbols.
- Cross-module steps describe how control or data moves between components, and every important edge has a verified call-site, assembly, binding, protocol, or test basis; otherwise it is labeled as interpretation or unknown.
- A lesson that explains a representative core flow contains a focused Mermaid call-flow diagram, and its nodes and edges match the verified source walkthrough.
- Mermaid syntax is well formed, labels are readable, and unknown relationships are not presented as verified facts.
- Project facts have local evidence; interpretations and unknowns are clearly distinguished.
- Code excerpts are minimal and accurate for the recorded source state.
- Design tradeoffs are supported rather than invented.
- Reflection questions are the final major section and test reasoning rather than recall alone.
- The prose uses the confirmed course language while code identifiers remain unchanged.

## Validate the complete course

- The output contains one outline and exactly the confirmed number of lesson files created by this workflow.
- Lesson numbering starts at the uniform-width representation of 1, such as `01` or `001`, is continuous, and has no duplicates.
- Filenames are safe and correspond to outline titles.
- No outline topic is silently omitted or replaced in the lesson files.
- Repeated material serves progression rather than accidental duplication.
- The course contains the required overall architecture or component diagram and the key call-flow diagrams for its representative core flows.
- Mermaid diagrams supplement rather than replace the prose explanations and source-reading routes.
- The full course satisfies the confirmed learning goal without drifting into excluded deployment or execution work.
- No user file was overwritten, deleted, or cleared.

## Validate partial modes

- **Outline only:** One complete outline was created and no lesson file was created or changed.
- **Selected lessons:** Exactly the requested lesson files were created, their numbers and titles match the confirmed outline, and unrequested lessons were untouched. Missing unrequested lessons are not an error.
- **Update existing lesson:** Only the explicitly requested lesson was changed, unless the user also authorized an outline change. The updated lesson still satisfies the complete lesson contract.
- A targeted update to an existing lesson counts as explicit authorization to write that file; it does not authorize overwriting or changing any unrelated file.

## Completion report

Report:

- output directory;
- output mode;
- outline file;
- created or updated lesson files;
- recorded source version and local state;
- validation performed;
- any fact, path, symbol, or flow that remains uncertain or unverified.

Do not claim completion if files required by the selected output mode are missing or a confirmation gate required by that mode was skipped.
