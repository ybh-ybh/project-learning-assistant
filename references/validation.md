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
- Referenced local documents and source paths exist.
- No lesson files or placeholders were created.

After these checks, report the outline and stop for explicit confirmation.

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
- Project facts have local evidence; interpretations and unknowns are clearly distinguished.
- Code excerpts are minimal and accurate for the recorded source state.
- Design tradeoffs are supported rather than invented.
- Reflection questions are the final major section and test reasoning rather than recall alone.
- The prose uses the confirmed course language while code identifiers remain unchanged.

## Validate the complete course

- The output contains one outline and exactly the confirmed number of lesson files created by this workflow.
- Lesson numbering starts at `01`, is continuous, and has no duplicates.
- Filenames are safe and correspond to outline titles.
- No outline topic is silently omitted or replaced in the lesson files.
- Repeated material serves progression rather than accidental duplication.
- The full course satisfies the confirmed learning goal without drifting into excluded deployment or execution work.
- No user file was overwritten, deleted, or cleared.

## Completion report

Report:

- output directory;
- outline file;
- lesson files;
- recorded source version and local state;
- validation performed;
- any fact, path, symbol, or flow that remains uncertain or unverified.

Do not claim completion if required lesson files are missing or the outline confirmation gate was skipped.
