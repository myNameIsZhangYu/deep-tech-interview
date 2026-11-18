# Deep Tech Interview Learning Method

## Goal

Rapidly learn a technology deeply enough to:

- Handle advanced interview follow-ups.
- Explain real production problems and solutions.
- Compare alternatives and justify tradeoffs.
- Transfer the underlying mechanism to other systems.

Core principle: do not passively consume tutorials. Build a question map,
absorb material to answer those questions, validate at the appropriate depth,
compare alternatives, produce interview-ready notes, and reinforce through
pressure-tested recall.

## Workflow

```text
0. Self-assessment
1. Scope
2. Question map and scorecard
3. Question-driven absorption and cross-validation
4. Validation design and graded verification
5. Comparable-technology tradeoff analysis
6. Production notes
7. Pressure-tested output
8. Spaced review
```

Exit when every A/B-level question scores at least 4, at least one A/B-level
concept has validation evidence, and the learner can pass the interview-output
checks. Stop then; do not keep expanding scope.

## 0. Self-assessment

Infer the learner's current level from conversation, existing notes, repositories,
and prior artifacts instead of requiring a questionnaire. State the assumption
explicitly. If the level is unknown, start at B-level:

```text
Assumed level: B.
Evidence: available context or the absence of prior artifacts.
```

Purpose: identify the starting level and avoid relearning known material without
making the first interaction unfriendly.

## 1. Scope

Answer three questions:

1. Where do interviewers usually ask about it: concept, system design, or
   troubleshooting?
2. Which production pain point does it solve?
3. What is the depth boundary: understand principles, explain tradeoffs, or
   modify source code?

Output: one page containing three questions that must be answerable after
learning.

Out-of-scope findings go into an "outside boundary" list. Do not chase them.

## 2. Question map and scorecard

Start with defaults immediately. The first response should contain a default
scope, a question map, and a plan, then one confirmation:

```text
Reply `continue` to execute this plan, or correct any default.
```

Do not open with multiple question groups. The initial map must contain at most
eight questions, distributed approximately as:

- Concept/principle: 2-3 questions.
- Design tradeoff: 2-3 questions.
- Production problem: 2-3 questions.

Do not list C-level questions unless the learner asks for broader coverage.

Build questions from real interview follow-ups and production scenarios, not
from a tutorial table of contents.

### Question layers

| Layer | Focus | Example |
|---|---|---|
| Concept/principle | What and why | How runtime state is persisted |
| Design tradeoff | Why this design and its cost | State machine versus pure LLM loop |
| Production problem | Failure, diagnosis, solution | Tool timeout, context overflow |

### Depth grading

- **A**: must be able to explain source-level or mechanism-level reasons.
- **B**: must be able to explain mechanics and tradeoffs.
- **C**: know the name and rough purpose.

### Scorecard

Score each question from 0 to 5:

| Score | Meaning |
|---|---|
| 0 | Cannot answer |
| 1 | Can repeat the definition |
| 2 | Can explain mechanism |
| 3 | Can explain tradeoffs |
| 4 | Can explain production problems and solutions |
| 5 | Can explain validation evidence |

Learning target: A/B-level questions reach score 4 or higher.

The instructor maintains the scorecard based on learner output, follow-up answers,
and validation evidence. Do not require the learner to score every question before
starting; show a consolidated scorecard after pressure testing or validation.

## 3. Question-driven absorption and cross-validation

Choose a reading mode based on topic maturity:

| Mode | Order | Use when |
|---|---|---|
| Mature technology | Official docs -> RFC/design doc -> source -> issues | Stable docs and community |
| New field | High-quality survey -> code examples -> docs -> source | New ecosystem, incomplete docs |
| Production troubleshooting | Issues/postmortems -> docs -> source | Goal is diagnosis ability |

While reading, immediately answer one question from the map in your own words.
Mark unresolved points as the next deep-dive targets. Do not read linearly
without connecting material to the question map.

Cross-validation rules:

- A/B-level conclusions need two independent sources, such as source plus docs
  or issues plus an engineering blog.
- C-level conclusions may use one source.
- Mark anything not cross-validated as "pending validation."

## 4. Validation design and graded verification

Before doing anything, write a validation plan:

```text
Hypothesis: I believe X works this way.
Expected: if true, I should observe ___.
Counter-case: if false, I should observe ___.
Failure signal: what indicates failure.
Diagnosis order: config / code / dependency / data / environment.
```

Choose effort by depth grade:

| Grade | Verification |
|---|---|
| A | Modify source, reproduce failure, or run a focused experiment |
| B | Run a minimal demo, typically 50-200 lines |
| C | Restate accurately; no implementation required |

When something fails, diagnose root cause rather than copying a fix:

```text
1. What exactly happened?
2. What did I expect, and why?
3. Where is the gap between expected and actual?
4. Can a minimal change reproduce it?
5. Which layer caused it: config, code, dependency, data, environment?
6. After fixing, what comparison proves that was the cause?
```

Record each validation as: what was done -> observed result -> explanation ->
pitfalls discovered.

## 5. Comparable-technology tradeoff analysis

Select two to four alternatives and compare them on the same dimensions:

| Dimension | Option A | Option B | Option C |
|---|---|---|---|
| Core abstraction | | | |
| What it solves | | | |
| What it does not solve | | | |
| Design tradeoff | | | |
| Performance/cost | | | |
| Learning cost | | | |
| Production risk | | | |
| Typical fit | | | |
| Typical anti-pattern / poor fit | | | |

Answer three questions:

1. Why choose A over B in this scenario?
2. Under what conditions is B better?
3. If redesigning, what would you change?

Pass criterion: can explain "because of X constraint, we choose Y; the cost
is Z."

## 6. Production notes

Create interview-ready notes, not reading summaries:

```text
[One-sentence positioning]
[Why needed] What happens without it
[Core mechanism] A diagram plus no more than three key points
[Production problems and solutions] At least three real pitfalls
[Comparison tradeoffs] Alternatives plus why choose or reject them
[Interview follow-up chain] 5-8 questions and your answers
[Validation evidence] Experiments, observations, and results
[Misconception list] Confident statements that turned out wrong
[Unknowns] Open points
```

A concept is considered consolidated when you can explain it in three minutes
without notes.

## 7. Pressure-tested output

Merge self-questioning, adversarial follow-ups, and teaching into one cycle.

### Three layers

1. **Self-questioning**: answer the follow-up chain below.
2. **Adversarial follow-up**: have an AI, peer, or mock interviewer ask three
   layers: why -> how implemented -> production issue.
3. **Teach**: write or deliver a ten-minute beginner explanation.

### Follow-up chain

```text
What is it and why is it needed?
What happens without it?
How is it implemented? Key data structures or flow?
What production issues arise?
How do you detect, solve, and justify the solution?
Where does it break first at 10x scale?
Is there a better alternative and why was it not chosen?
What are comparable options and their key differences?
If redesigning, what would you change?
Where else can this mechanism transfer?
How was the conclusion validated? How would you discover a wrong assumption?
```

### Recall test

Explain one concept in three minutes without notes. Add stuck points to the
next-round list and incorrect statements to the misconception list.

### Transfer and reverse questioning

For every A-level concept, ask where the mechanism can transfer to another
system. Then create five follow-up questions yourself and answer them.

## 8. Spaced review

Use active recall, not rereading:

| Day | Recall task |
|---|---|
| 3 | One-sentence positioning, two production pitfalls, one tradeoff |
| 7 | Full follow-up chain with a three-minute timer |
| 21 | Teach it once through a beginner explanation |

After each review, update the pending list and misconception list.

## Completion criteria

A topic is complete only when all are true:

- Every A/B-level question scores 4 or higher.
- At least one A/B-level concept has validation evidence.
- You can explain the core mechanism in three minutes without notes.
- You can answer at least three production problems and solutions.
- You can compare alternatives and justify a selection.
- You can say where the mechanism transfers to other systems.

## Anti-patterns

| Anti-pattern | Correction |
|---|---|
| Read the full tutorial first | Build the question map first and read purposefully |
| Treat understanding as mastery | Perform at least one graded validation |
| Accumulate notes but cannot explain | Produce interview-ready notes and recall aloud |
| Pursue depth while ignoring production issues | Prioritize real failure modes and solutions |
| Study everything broadly but shallowly | Deep-dive within scope; label the rest outside boundary |
| Keep learning because it feels productive | Follow the scorecard exit rule |
| Repeat a confidently wrong explanation | Maintain and resolve the misconception list |

## Light Mode

Use when the learner asks for a quick pass, an overview, or explicitly asks you
not to ask questions:

1. Infer scope and depth boundary.
2. Produce a six-question map focused on A/B-level concepts.
3. Produce an interview-ready summary: positioning, why needed, core mechanism,
   production pitfalls, and one comparison tradeoff.
4. List suggested validation experiments, but do not run them.
5. Do not run pressure testing unless requested.
