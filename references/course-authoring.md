# Course Authoring Contract

Apply this contract when creating the outline, revising it, or generating lessons. Translate user-facing headings and prose into the confirmed course language. Keep code identifiers and project paths unchanged.

## Outline filename and header

Use an all-zero prefix at the same width as the lesson numbers, with a minimum width of two digits, and a localized outline title. For courses with no more than 99 lessons, use `00`; for larger courses, expand the width, for example:

```text
00_<localized-outline-title>.md
00_course-outline.md
000_<localized-outline-title>.md
```

The outline header must make the analysis baseline visible near the top:

```markdown
# <Project Name> Course Outline (<N> Lessons)

> Local project: `<absolute local path>`
> Source origin: `<locally confirmed origin, or omit this line>`
> Project version: `<tag/release/branch and commit, or version unknown>`
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

Include at least one Mermaid diagram that shows the project's overall architecture or component relationships. Explain the diagram's scope and the important relationships in prose.

The outline must cover the important architecture, modules, core mechanisms, source entry points, and end-to-end behavior needed for the confirmed goal. Completeness means conceptual coverage, not mentioning every file.

## Mermaid diagrams

Use fenced `mermaid` blocks for diagrams.

- The outline must contain an overall architecture or component-relationship diagram based on the actual local project structure.
- A lesson that explains a representative core flow must contain a key call-flow diagram based on the relevant source code. Do not force a diagram into lessons that have no meaningful call flow.
- Use `flowchart` for structural, dependency, request-flow, or data-flow relationships. Use `sequenceDiagram` when ordered interactions between participants are the clearest representation.
- Keep diagrams focused on the relationships needed for the current explanation. Split an unreadably dense diagram instead of turning it into a complete repository map.
- Every project-specific node must correspond to a verified local module, component, file, type, function, interface, route, event, datastore, or external boundary represented in the project.
- Every project-specific edge must be supported by a call site, dependency registration, assembly code, protocol or route binding, event subscription, serialization contract, configuration, test, or local project documentation.
- If an edge is inferred rather than directly verified, label it as an interpretation in the surrounding prose. Do not draw an unknown relationship as a verified fact.
- Use clear, localized human-facing labels while preserving exact code identifiers when they are important to the explanation.
- Check that each Mermaid block has valid diagram syntax, stable node identifiers, balanced delimiters, and no unsupported placeholder text.

Introduce or follow every diagram with a prose explanation and the relevant source evidence. A diagram supplements the mechanism explanation and source walkthrough; it never replaces either one.

## Lesson filename

Use continuous, uniform-width numbering with at least two digits and a localized filesystem-safe title. Expand the width when the course has more than 99 lessons:

```text
01_<lesson-title>.md
02_<lesson-title>.md
...
100_<lesson-title>.md
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

When the lesson explains a representative core source flow, place its Mermaid call-flow diagram in the relevant mechanism section before the detailed source walkthrough.

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

## Partial generation and lesson updates

- **Outline only:** Create the complete outline and no lesson files. The outline does not need approval unless the user later requests lesson generation.
- **Selected lessons:** Use the confirmed outline's existing number and title for each requested lesson. Generate only those files and do not create placeholders for the rest.
- **Update existing lesson:** Preserve the course language, numbering, and outline alignment. Modify only the explicitly requested lesson. If the request changes course structure, update the outline and obtain confirmation before applying the structural lesson change.

All generated or updated lessons must still satisfy the full lesson structure, Mermaid, source-grounding, and reflection-question requirements.
