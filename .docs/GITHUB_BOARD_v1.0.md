# GitHub Board v1.0 — Progress View Derived From Engineering Roadmap v1.0

Status: DERIVED VIEW — NOT SOURCE OF TRUTH
Version: 1.0
Date: 2026-09-27
Derived from: Engineering Roadmap v1.0 Frozen
Rule: On any conflict, the roadmap wins. This board tracks progress only and must never reinterpret acceptance criteria.

Purpose: Give a distracted builder a kanban motion system with urgency rails, without duplicating architectural decisions. All meaning lives in the roadmap. All motion lives here.

Prose only rule: This file contains no ready to paste commands and no configuration contents. It describes titles, bodies, labels, and column movement in words so the builder creates items manually and learns the tool. Result over procedure applies here as well.

---

## 1. Proposed GitHub Structure — Option A

Eight milestones, one per roadmap stage, named Stage Zero through Stage Seven with matching timeboxes and deadlines counted from start date. One GitHub Project board of type board with six columns in this exact order: Backlog, Study, Building, Chaos and Load Proving, Interview Gate, Done.

Milestones own deadlines and exit conditions. Issues own work. The board owns motion. Labels own priority and type. No issue lives outside a milestone. No milestone is closed until its interview gate is passed.

Suggested labels to create manually:

- Type Study, Type Build, Type Proving, Type Gate, Type Retro
- Priority High, Priority Medium
- Area Game Server, Area Matchmaking, Area Presence, Area Events, Area Durability, Area Observability, Area Edge
- Risk Single Point Of Failure, Risk State Loss, Risk Partition, Risk Overload

Suggested estimate field: use a simple size in the issue body described in words as Small, Medium, or Large relative to six to ten hours per week, not story points.

---

## 2. Milestones Catalog

Create each milestone manually with a title, description in your own words paraphrasing the roadmap, start plus due date from the timebox, and a written exit condition that quotes the roadmap gate in spirit.

- Milestone Stage Zero Naive Monolith Built To Die, duration one week. Description: single process playground that must collapse informatively. Exit: postmortem written plus gate passed.
- Milestone Stage One Observability Before Scale, duration two weeks. Description: structured logs plus graphs before any scaling. Exit: minimal survival graphs proven under flood plus gate passed.
- Milestone Stage Two State Separation And Durability, duration two weeks. Description: ephemeral versus durable line with idempotent commit. Exit: retry storm shows single effect plus gate passed.
- Milestone Stage Three Horizontal Nodes With Presence, duration two to three weeks. Description: multi node with presence and balancer affinity. Exit: single node termination isolates blast plus gate passed.
- Milestone Stage Four Events And Matchmaking, duration two weeks. Description: dedicated matchmaking plus event decoupling. Exit: consumer pause and replay converge singly plus gate passed.
- Milestone Stage Five Resilience Habits, duration two to three weeks. Description: timeouts retries shutdown bulkheads. Exit: rolling restart preserves lobby plus gate passed.
- Milestone Stage Six Partitioning And Chaos, duration two to three weeks. Description: deterministic placement plus injected partitions. Exit: chaos log with at least three drills plus gate passed.
- Milestone Stage Seven Soak And Graduation, duration three weeks. Description: full bot soak with mid soak faults plus operating notes. Exit: soak plus final defense passed.

Set due dates immediately on creation to create urgency. If a milestone slips by more than one week, add a retro issue rather than shifting all future milestones silently.

---

## 3. Issue Templates — What To Create Per Milestone

For each milestone, create the following issues manually. Titles are suggested verbatim. Bodies are described so you write them in your own words.

### 3A. Study Issues, One Per Major Concept Group

Example titles for Stage Zero: Study Authoritative Tick And Transport Intuition. Study Event Loop Starvation And Fate Sharing. Study Ephemeral Versus Durable. Study Docker Services Networks Volumes Basics.

Body shape for every study issue: Goal in one sentence. Key questions to answer, three to five. Documentation to read, listed by title. Done definition: can whiteboard the mechanism plus can name one failure mode plus can name one trade off. Keep bodies short. Move from Backlog to Study when reading starts, to Done only when you can defend without notes.

### 3B. Build Issues, One Per Acceptance Criterion

Translate each roadmap acceptance criterion into one build issue. Example titles for Stage Two: Durable Accounts Survive Restart While Matches Vanish By Design. Double Submitted Result Records Single Effect. Slow Persistence Causes Bounded Shedding With Healthy Ticks. Dead Sockets Reaped Deterministically.

Body shape: Desired observable result paraphrased from roadmap. Evidence to attach, described as log field names, graph names, and durable state checks in words. Explicit non goal paraphrased from anti goals. Done definition: criterion observable on Compose plus evidence described in a comment plus gate style self check passed.

### 3C. Proving Issues, Chaos And Load

Stages Zero through Two have one proving issue each focused on flood or termination observation. Stages Three through Seven have at least two proving issues each, one for termination and one for partition or soak.

Example titles: Flood Two Matches And Prove Fate Sharing. Terminate App Mid Match And Prove Total Loss. Terminate One Game Node And Prove Isolation. Partition Presence And Prove Clean Abort. Pause Consumer And Prove Lag Recovery. Soak Twenty Matches With Bots And Mid Soak Fault.

Body shape: Hypothesis in one sentence. Fault to inject described by affected logical groups in words, not steps. Abort condition in words. Expected healthy versus affected behavior. Evidence to capture. Done definition: hypothesis confirmed or refuted with a learning note, no silent green check.

### 3D. Gate Issue, One Per Milestone

Title pattern: Gate Stage X Defense. Body contains the roadmap example defense questions paraphrased, plus your own two questions, plus verdict field left empty until mentorship judges. Only mentorship sets Pass or Retry With Pointer. On Retry, create a follow up study issue linked to the gate issue rather than reopening old work silently.

### 3E. Retro Issue On Overrun Only

Title pattern: Retro Stage X Overrun. Create only if the milestone exceeds its timebox by more than one week. Body: what blocked, what was misunderstood, what changes in routine, with no scope cut to the next milestone.

---

## 4. Board Workflow — How Cards Move

Backlog holds all not started issues for the current plus next milestone only. Do not load the entire roadmap onto the board at once or the board becomes wallpaper.

Study holds active learning issues. Limit to two at a time to protect focus for an easily distracted builder.

Building holds active implementation issues. Limit to one at a time. If blocked, write the blocker as a comment and move only that card back to Backlog, never sideways.

Chaos and Load Proving holds active fault drills. Nothing enters here until its related build issue is functionally complete. This enforces prove after build.

Interview Gate holds the gate issue plus any linked retry follow ups. Nothing enters Done until the gate issue for that milestone is marked Pass by mentorship.

Done holds only closed issues with evidence comments. A closed issue without an evidence comment is reopened.

Weekly routine: pick the milestone, pull one study plus one build, finish, prove, defend. Update the Project board at the start and end of each session, not mid flow.

---

## 5. Copy Paste Helper — Issue Body Skeleton Described In Words

Since automation is banned by your contract, create each issue by hand using this skeleton, written in your own words:

First line: goal as a single sentence starting with Prove or Learn or Harden.

Second paragraph: context linking back to the roadmap stage and criterion by name.

Third section: bulleted list of observable done signals, each starting with Observable followed by the result.

Fourth section: bulleted list of evidence to attach, naming log fields, graph titles, and durable checks in words.

Final line: non goal paraphrased from the roadmap anti goals for that stage.

No code, no pasted logs, no pasted configs in issue bodies. Describe evidence, do not dump it. Link longer notes as attached markdown files in the future code repository if needed, keeping this docs folder outside the repo per your placement rule.

---

## 6. Anti Drift Rules

The roadmap is immutable. If a board issue suggests a smarter architecture, do not edit the roadmap. Finish the stage as specified, pass the gate, then propose a versioned roadmap amendment as a separate discussion with rationale and migration cost. Most such ideas will correctly wait until after graduation.

If GitHub renames features from milestones or projects to new terms, adapt names but keep the mapping: one timebox with exit gate per stage, one motion board with the six columns above.

Close a milestone only on gate Pass. Never close on calendar expiry. Calendar creates urgency, gates create truth.

---

End of GitHub Board v1.0. Derived view.
