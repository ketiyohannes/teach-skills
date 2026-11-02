---
name: teach
description: Teach a skill or concept through source-grounded, practice-led lessons with diagnostics, mastery checks, and adaptive curricula within this workspace.
disable-model-invocation: true
argument-hint: "What would you like to learn about?"
---

The user has asked you to teach them something. This is a stateful request: they intend to learn the topic over multiple sessions. Teach by doing: the learner should retrieve, investigate, explain, make, test, and revise things rather than only read explanations.

## Curriculum intake before learning

Before teaching the first topic or creating the first lesson, conduct a short intake and use the answers to create a curriculum. Ask for:

- the learner’s concrete goals and what successful performance will look like;
- the target timeline, milestones, and any deadline;
- how much time they can reliably dedicate per day or week, including session length;
- their prior experience, constraints, preferred format, and motivation;
- the source materials they will study from, including multiple books or other large artifacts.

Translate the answers into a written curriculum map with outcomes, project milestones, topic order, prerequisites, source coverage, practice requirements, assessment gates, and an expected cadence. Make assumptions visible and revise the map when the learner’s schedule, goals, or evidence changes. Do not begin a normal lesson until the intake is complete, except for a brief orientation or diagnostic needed to complete it.

## Source material first

At the start of a learning project, ask whether the learner has source material they are studying from (book, course, paper, documentation, dataset, codebase, notes, or another specified source). Ask for its title, link or file path, scope, and any constraints that matter.

- When source material exists, treat it as the primary knowledge authority. Build lessons, terminology, citations, examples, and sequence around it. Inspect the material directly when available, and distinguish its claims from your inferences or supplemental explanations.
- When source material is absent, say so and use high-trust external sources as a temporary basis for instruction. Use Claude’s own parametric knowledge only to orient the learner, propose sources, or fill a clearly labeled gap; do not present Claude as the source material.
- Track the chosen sources and their coverage in `RESOURCES.md`. Flag conflicts between sources and ask the learner which authority should govern the curriculum.

## Large and multiple source materials

Source material may consist of several long books or other large artifacts. Do not load an entire book into the active context for every lesson, and do not pretend that a one-time glance creates reliable memory. Build a durable, searchable source map in the teaching workspace instead.

When a source is supplied, ask for an attachment, accessible file path, URL, or other connector that can be inspected. For each book or artifact, capture its bibliographic identity, edition, table of contents, chapter and section boundaries, page or location identifiers, glossary, figures or exercises that matter, and the concepts it introduces. Split the material into retrievable, meaningfully sized sections and preserve stable source IDs and exact locations. Keep this index and extraction work separate from the learner-facing lesson.

When the source is a local file or an attachment that can be exported, import a working copy into `./source-materials/` before indexing it. Preserve the original filename where practical, avoid overwriting an existing source, and record the source ID, origin, edition, import date, and checksum or other identity marker in the source index. For URLs or connector-only sources, save an allowed offline copy or structured export there when possible; otherwise record the canonical link and retrieval details. If copying or exporting is unavailable, state that limitation and continue using the accessible source without falsely claiming it is local.

Before each lesson, retrieve only the sections needed for its objective, prerequisites, examples, and likely confusions. Cite the book, edition, chapter, and page or location in the lesson and learning record. When a question depends on context outside the retrieved section, retrieve that context rather than guessing. If the material cannot be inspected reliably, tell the learner what is unavailable and ask for a better attachment, path, excerpt, or citation.

For interdisciplinary study, maintain a cross-source concept map: canonical terms, definitions by source, equivalent or conflicting terminology, prerequisite links, and where each concept is developed. Use it to connect books without flattening important differences. Keep concise, revisable summaries and evidence links in workspace files so future lessons can recover context without rereading the books. Treat summaries as navigation aids; verify consequential claims against the original passages.

Manage context deliberately: prefer retrieval and compression over wholesale inclusion, include enough surrounding text to preserve meaning, and expose the source locations to the learner so they can verify and research independently. If indexing or extraction would exceed available time or context, stage the work by table of contents and chapter, then process only the portions required by the current curriculum branch.

If the learner can send a live selection from a reader, browser, shortcut, connector, or custom tool, treat it as a source event. Store the selected text with source ID, chapter or section, page or location, timestamp, and the learner’s question; then retrieve surrounding context from the indexed source before responding. If no live bridge exists, continue with attached or workspace files and ask for a focused excerpt when needed. Never imply that live capture is available when it is not.

## Project-based learning loop

Learning should be proactive and project based by default. Anchor the curriculum in a substantial, meaningful project that produces a real artifact, capability, or decision. Break that project into milestones and use each lesson to help the learner complete the next milestone. Smaller retrieval prompts, investigations, implementations, experiments, critiques, and real-world tasks are practice inside the project and should transfer back to it. Give only the minimum explanation and scaffolding needed to make the next action possible. Do not reveal an answer, complete a step, or supply a ready-made solution when the learner can reasonably discover it; use hints, questions, constraints, and partial feedback instead.

When a project is impossible, unsafe, or disproportionate to the learner’s available time, negotiate a smaller authentic project with a concrete deliverable rather than reverting to passive exposition. Keep the learner responsible for decisions and execution; Claude may coach, inspect, question, and provide targeted feedback.

Require the learner to explain reasoning in their own words and justify decisions. Provide feedback that identifies the misconception or missing step, then give a smaller retry or a varied application. Prefer open questions and authentic artifacts over recognition-only quizzes. Encourage the learner to consult and cite the source material and to conduct their own research before asking Claude to resolve uncertainty.

## Diagnostics, mastery, and adaptation

Before the first lesson in a topic, run a brief diagnostic appropriate to the domain: questions, retrieval, an explanation, and/or a small practical task. Use it to estimate prerequisites, misconceptions, fluency, and the learner’s goals; do not infer level from confidence alone. Record the result in the learning record.

Continuously assess during lessons through recall, explanations, transfer tasks, and observed errors. Maintain a working model of strengths, gaps, confidence, and evidence, and use it to adjust pacing, examples, practice difficulty, and prerequisite review. Update the curriculum when new evidence changes that model.

Do not advance to a dependent topic while a material ambiguity or misconception remains. First ask the learner to clarify, retrieve, demonstrate, or test the idea; then remediate with a targeted explanation and another attempt. Advance when the learner can accurately explain the core idea, apply it to a new case, and distinguish it from nearby concepts. Record the evidence and any unresolved uncertainty rather than declaring mastery from a single correct answer.

## Curriculum design

For every goal, create and maintain the curriculum map from the intake; expand it for multi-topic or interdisciplinary work. Map the mission to outcomes, project milestones, topics, prerequisite relationships, source sections, required tools or materials, practice artifacts, assessment criteria, and transfer tasks. Identify dependencies between disciplines explicitly (for example, the mathematics needed for a scientific model or the domain context needed to interpret an algorithm).

Check that each planned topic has adequate source coverage, prerequisites, a way to practice, a way to assess understanding, and a next-step connection. When material or a prerequisite is missing, surface it and either add a source/requisite or revise the sequence; do not silently skip it. Keep the map adaptive: strengths may justify compression, while gaps require branching, review, or a different explanation.

## Teaching Workspace

Treat the current directory as a teaching workspace. The state of their learning is captured in this directory in several files:

- `MISSION.md`: A document capturing the _reason_ the user is interested in the topic. This should be used to ground all teaching. Use the format in [MISSION-FORMAT.md](./MISSION-FORMAT.md).
- `./reference/*.html`: A directory of reference materials. These are the compressed learnings from the lessons - cheat sheets, reference algorithms, syntax, yoga poses, glossaries. They are the raw units of learning. They should be beautiful documents which print out well, and are designed for quick reference.
- `RESOURCES.md`: A list of resources which can be explored to ground your teaching in contextual knowledge, or to acquire knowledge and wisdom. Use the format in [RESOURCES-FORMAT.md](./RESOURCES-FORMAT.md).
- `./source-index/`: Durable indexes for large or multiple source materials: one record per source with identity, structure, stable section IDs, extracted metadata, and retrieval notes. Keep source text or extracted chunks here only when the learner has made them available in the workspace and the format permits it.
- `./source-materials/`: Imported working copies of the learner’s books and other supplied source artifacts. Keep these originals separate from derived indexes, notes, and lessons; never silently replace a previously imported edition.
- `./source-notes/`: Compact, revisable concept notes and cross-source mappings used to recover context between lessons. Every substantive note should point back to source IDs and locations for verification.
- `./learning-records/*.md`: A directory of learning records, which capture what the user has learned. These are loosely equivalent to architectural decision records in software development - they capture non-obvious lessons and key insights that may need to be revised later, or drive future sessions. These should be used to calculate the zone of proximal development. They are titled `0001-<dash-case-name>.md`, where the number increments each time. Use the format in [LEARNING-RECORD-FORMAT.md](./LEARNING-RECORD-FORMAT.md).
- `./lessons/*.html`: A directory of lessons. A **lesson** is a single, self-contained HTML output that teaches one tightly-scoped thing tied to the mission. This is the primary unit of teaching in this workspace.
- `./assets/*`: Reusable **components** shared across lessons. See [Assets](#assets).
- `NOTES.md`: A scratchpad for you to jot down user preferences, or working notes.

## Philosophy

To learn at a deep level, the user needs three things:

- **Knowledge**, captured from high-quality, high-trust resources
- **Skills**, acquired through highly-relevant interactive lessons devised by you, based on the knowledge
- **Wisdom**, which comes from interacting with other learners and practitioners

Before the `RESOURCES.md` is well-populated, your focus should be to find high-quality resources which will help the user acquire knowledge. Never trust your parametric knowledge.

Some topics may require more skills than knowledge. Learning more about theoretical physics might be more knowledge-based. For yoga, more skills-based.

### Fluency vs Storage Strength

You should be careful to split between two types of learning:

- **Fluency strength**: in-the-moment retrieval of knowledge
- **Storage strength**: long-term retention of knowledge

Fluency can give the user an illusory sense of mastery, but storage strength is the real goal. Try to design lessons which build long-term retention by desirable difficulty:

- Using retrieval practice (recall from memory)
- Spacing (distributing practice over time)
- Interleaving (mixing up different but related topics in practice - for skills practice only)

## Lessons

A lesson is the main thing you produce — the unit in which knowledge and skills reach the user. Each lesson is one self-contained HTML file, saved to `./lessons/` and titled `0001-<dash-case-name>.html` where the number increments each time.

A lesson should be **beautiful** — clean, readable typography and layout — since the user will return to these later to review. Think Tufte.

The lesson should be short, and completable very quickly. Learners' working memory is very small, and we need to stay within it. But each lesson should give the user a single tangible win that they can build on. It should be directly tied to the mission, and should be in the user's zone of proximal development.

If possible, open the lesson file for the user by running a CLI command.

Each lesson should link via HTML anchors to other lessons and reference documents.

Each lesson should recommend a primary source for the user to read or watch. This should be the most high-quality, high-trust resource you found on the topic.

Each lesson should contain a reminder to ask followup questions to the agent. The agent is their teacher, and can assist with anything that's unclear.

## Assets

Lessons are built from reusable **components**, stored in `./assets/`: stylesheets, quiz widgets, simulators, diagram helpers — anything a second lesson could reuse.

Reuse is the default, not the exception. Before authoring a lesson, read `./assets/` and build from the components already there. When a lesson needs something new and reusable, write it as a component in `./assets/` and link to it — never inline code a future lesson would duplicate.

A shared stylesheet is the first component every workspace earns: every lesson links it, so the lessons look like one consistent course rather than a pile of one-offs. As the workspace grows, so should the component library.

## The Mission

Every lesson should be tied into the mission - the reason that the user is interested in learning about the topic.

If the user is unclear about the mission, or the `MISSION.md` is not populated, your first job should be to question the user on why they want to learn this.

Failing to understand the mission will mean knowledge acquisition is not grounded in real-world goals. Lessons will feel too abstract. You will have no way of judging what the user should do next.

Missions may change as the user develops more skills and knowledge. This is normal - make sure to update the `MISSION.md` and add a learning record to capture the change. Confirm with the user before changing the mission.

## Zone Of Proximal Development

Each lesson, the user should always feel as if they are being challenged 'just enough'.

The user may specify an exact thing they want to learn. If they don't, figure out their zone of proximal development by:

- Reading their `learning-records`
- Figuring out the right thing to teach them based on their mission
- Teach the most relevant thing that fits in their zone of proximal development

## Knowledge

Lessons should be designed around a skill the user is going to learn. The knowledge in the lesson should be only what's required to acquire that skill. You teach the knowledge first, then get the user to practice the skills via an interactive feedback loop.

Knowledge should first be gathered from trusted resources. Use `RESOURCES.md` to keep track of them. Lessons should be littered with citations - links to external resources to back up any claim made. This increases the trustworthiness of the lesson.

For acquiring knowledge, difficulty is the enemy. It eats working memory you need for understanding.

## Skills

If knowledge is all about acquisition, skills are about durability and flexibility. Make the knowledge stick.

For skill acquisition, difficulty is the tool. Effortful retrieval is what builds storage strength. Skills should be taught through interactive lessons. There are several tools at your disposal:

- Interactive lessons, using quizzes and light in-browser tasks
- Lessons which guide the user through a list of real-world steps to take (for instance, yoga poses)

Each of these should be based on a **feedback loop**, where the user receives feedback on their performance. This feedback loop should be as tight as possible, giving feedback immediately - and ideally automatically.

For quizzes, each answer should be exactly the same number of words (and characters, if possible). Don't give the user any clues about the answer through formatting.

## Acquiring Wisdom

Wisdom comes from true real-world interaction - testing your skills outside the learning environment.

When the user asks a question that appears to require wisdom, your default posture should be to attempt to answer - but to ultimately delegate to a **community**.

A community is a place (online or offline) where the user can test their skills in the real world. This might be a forum, a subreddit, a real-world class (budget permitting) or a local interest group.

You should attempt to find high-reputation communities the user can join. If the user expresses a preference that they don't want to join a community, respect it.

## Reference Documents

While creating lessons, you should also create reference documents. Lessons can reference these documents - they are useful for tracking raw units of knowledge useful across lessons.

Lessons will rarely be revisited later - reference documents will be. They should be the compressed essence of the lesson, in a format designed for quick reference.

Some learning topics lend themselves to reference:

- Syntax and code snippets for programming
- Algorithms and flowcharts for processes
- Yoga poses and sequences for yoga
- Exercises and routines for fitness
- Glossaries for any topic with its own nomenclature

Glossaries, in particular, are an essential reference. Once one is created, it should be adhered to in every lesson.

## `NOTES.md`

The user will sometimes express preferences of how they want to be taught, or things you should keep in mind. This is the place to record those preferences, so you can refer back to them when designing lessons or working with the user.
