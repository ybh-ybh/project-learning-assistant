# Course Authoring Contract

Apply this contract when creating the outline, revising it, or generating lessons. Translate user-facing headings and prose into the confirmed course language. Keep code identifiers and project paths unchanged.

## Outline filename and header

Use a two-digit `00` prefix and a localized outline title, for example:

```text
00_<localized-outline-title>.md
00_course-outline.md
```

The outline header must make the analysis baseline visible near the top:

```markdown
# <Project Name> Course Outline (<N> Lessons)

> Local project: `<absolute local path>`
> Source origin: `<locally confirmed origin, or omit this line>`
> Project version: `<tag/release/branch and commit, or local snapshot; version unknown>`
> Local state: `<clean, or includes local modifications>`
> Course language: `<language>`
> Learning goal: `<confirmed goal>`
> Outline status: Awaiting user confirmation
```

Use localized values and labels in the generated course. The absolute local path belongs in the outline metadata; source-reading routes inside lessons should use paths relative to the project root.

After explicit confirmation, change only the status to a localized equivalent of `Confirmed by user`. A status-only change does not alter the approved course design. If any topic, order, scope, or lesson count changes, request confirmation again.

## Required outline content

The outline must include:

1. overall learning outcomes;
2. the learning strategy or conceptual through-line;
3. a course directory containing every lesson number, title, core question, and main project coverage;
4. a recommended reading order or progression explanation;
5. the common lesson structure;
6. important local reference documents or source entry points when useful.

Include a compact text-based learning map when it materially clarifies dependencies. Do not require Mermaid in this version.

The outline must cover the important architecture, modules, core mechanisms, source entry points, and end-to-end behavior needed for the confirmed goal. Completeness means conceptual coverage, not mentioning every file.

## Lesson filename

Use continuous two-digit numbering and a localized filesystem-safe title:

```text
01_<lesson-title>.md
02_<lesson-title>.md
...
```

Remove characters that are invalid for the target filesystem. Keep the filename recognizably aligned with the title in the outline.

## Required lesson structure

Use this semantic structure, translated into the confirmed course language:

```markdown
# Lesson <NN>: <Title>

## Learning Objectives

<!-- This must be the first major section. -->

## <Concept, Architecture, or Mechanism Sections>

## Source Walkthrough

## Design Decisions and Tradeoffs

## Reflection Questions

<!-- This must be the final major section. -->
```

The middle sections should follow the subject rather than a fixed count. A lesson may include concise examples or comparison tables when they improve understanding.

## Learning objectives

Write observable objectives. Prefer verbs such as explain, trace, compare, identify, and reason about. Objectives should describe what the learner will understand after the lesson, not what files the lesson will mention.

## Explanatory content

Teach the mechanism before sending the learner into code. Define project-specific terms, connect the lesson to earlier concepts, and explain why the selected source path matters.

Do not turn a lesson into:

- a directory listing;
- a sequence of unexplained code excerpts;
- generic domain theory that is not tied to the local project;
- deployment instructions when the confirmed goal excludes deployment.

## Source walkthrough

Give a dependency-aware reading route. For each important step, include:

- a real path relative to the project root;
- the relevant class, function, interface, configuration key, or other symbol when available;
- what the learner should look for;
- how it connects to the preceding and following step.

For every important call or data-flow edge, verify the relationship itself rather than only the existence of both endpoints. Suitable evidence includes a direct call site, dependency registration or assembly code, protocol or route binding, event subscription, serialization contract, or a test that demonstrates the connection. If the edge cannot be verified, label it as an interpretation or unknown.

Use line numbers only when they add value and remain tied to the recorded source version. Verify every cited path and important symbol against the local project.

Use only the minimum code excerpt needed to explain a mechanism. Preserve original identifiers and syntax. Do not reproduce large portions of the repository.

## Facts, interpretations, and unknowns

State locally verifiable behavior directly. Mark architectural intent inferred from structure with language such as `This suggests...` or `This can be understood as...`, translated into the course language.

Never present an inference as an author's stated intention. If local documentation and source code disagree, describe the disagreement and use the recorded local source state as the implementation baseline. State unresolved information explicitly.

## Design decisions and reflection questions

Discuss design decisions only when local evidence or a defensible comparison supports them. Avoid generic praise.

End each lesson with questions that test reasoning, such as:

- explaining why a boundary exists;
- tracing a request or data lifecycle;
- predicting the effect of a code change;
- comparing the chosen design with a plausible alternative;
- identifying evidence for a project-specific conclusion.

Do not place references, summaries, or any other major section after the reflection questions.
