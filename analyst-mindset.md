# Analyst Mindset

## Purpose

This document explains the mindset behind effective requirements gathering.

The goal of a Business Analyst is not to fill out templates, collect feature requests, or act as an order taker. The analyst’s job is to understand the business problem deeply enough to identify missing information, uncover assumptions, predict failure points, and define a workable path forward.

Templates, user stories, acceptance criteria, and backlog items are outputs of analytical thinking — not substitutes for it.

---

# The Core Principle

## Filling out the template is not the job.

The job is the thinking that happens before anything gets written down.

A completed template does not prove understanding.

A good analyst:
- asks better questions,
- identifies missing information,
- challenges assumptions,
- reasons through edge cases,
- evaluates risk,
- and helps stakeholders clarify what they actually need.

The documentation exists so people who were not in the room can understand:
- the problem,
- the intent,
- the logic,
- the risks,
- the assumptions,
- and the expected outcome.

---

# The Difference Between an Order Taker and an Analyst

## The Order Taker

An order taker hears:

> “We need this automated.”

Then writes:

> “Build automation.”

The order taker assumes:
- the stakeholder already understands the problem,
- the requested solution is correct,
- all needed information exists,
- and the implementation details will work themselves out later.

This creates fragile systems and unclear requirements.

---

## The Analyst

An analyst hears:

> “We need this automated.”

Then starts asking:

- What problem are we actually solving?
- What triggers this process?
- What information enters the process?
- What decisions need to be made?
- What data supports those decisions?
- What happens when information is missing?
- What happens if the system makes the wrong decision?
- Who is affected by failure?
- What outcome are we actually trying to achieve?

The analyst does not simply document requests.

The analyst stress-tests the logic of the request.

---

# The IPO Model: Input → Process → Output

One of the simplest and most effective ways to analyze a workflow is:

1. Input
2. Process
3. Output

This model helps analysts reason through systems even when information is incomplete.

---

# 1. Input

Inputs are the information, files, records, events, forms, or actions that enter the process.

The analyst must determine:
- what information exists,
- whether it is reliable,
- whether it is complete,
- and whether it is sufficient to support the decisions that must be made.

## Questions to Ask

- What starts this process?
- What data enters the system?
- Where does the data come from?
- Which system is the source of truth?
- Which fields are reliable?
- Which fields are user-entered or inconsistent?
- What information might be missing?
- Do we have enough information to make the decisions we need to make?

## Important Principle

Never assume the input data is perfect.

People mistype names.
Records become duplicated.
Folders do not exist.
Users misunderstand forms.
Documents are incomplete.
Systems drift out of sync.

A strong analyst assumes imperfect reality.

---

# 2. Process

The process is the set of decisions, rules, validations, workflows, and business logic applied to the inputs.

This is where analysts provide the most value.

The analyst must understand:
- what decisions are being made,
- what rules control those decisions,
- how uncertainty is handled,
- and what happens when something goes wrong.

## Questions to Ask

- What decisions need to be made?
- Based on what information?
- What business rules apply?
- What assumptions are we making?
- Can we infer missing information?
- Can we safely use a default?
- What happens if the decision is wrong?
- How would we detect an incorrect decision?
- What edge cases exist?
- What should happen when the system is uncertain?

## Important Principle

Requirements gathering is not about defining the happy path.

It is about understanding:
- ambiguity,
- uncertainty,
- exceptions,
- and operational risk.

---

# 3. Output

Outputs are the results of the process.

The analyst must determine whether the process actually solves the intended business problem.

## Questions to Ask

- What should happen at the end?
- What should be created, updated, moved, sent, displayed, or logged?
- Who needs visibility into the result?
- How do we know the process succeeded?
- What should happen if the process fails?
- Does the output actually solve the original problem?

## Important Principle

Do not confuse activity with value.

Moving a file is not the goal.

The goal is:
- making the document accessible,
- reducing manual effort,
- improving accuracy,
- supporting operational visibility,
- or enabling downstream work.

The output must support the business outcome.

---

# Working With Incomplete Information

Real-world requirements gathering rarely happens with perfect information.

Stakeholders:
- may not fully understand their own process,
- may describe symptoms instead of root causes,
- may request incorrect solutions,
- may omit critical details,
- or may not know the answers to important questions.

The analyst must still move the conversation forward.

## Good Analysts Know How To:

- identify missing information,
- make reasonable inferences,
- document assumptions,
- flag uncertainty,
- and determine what must be clarified before implementation.

The goal is not perfect knowledge.

The goal is sufficient understanding to define the next useful step.

---

# Assumptions Are Not Failures

Analysts frequently need to make assumptions.

The key is:
- knowing when you are assuming,
- documenting the assumption,
- understanding the risk,
- and validating it later when possible.

## Example

Assumption:
> “The resource record ID uniquely identifies the correct person.”

Questions:
- Is that always true?
- What happens if duplicate records exist?
- What happens if the ID is missing?
- What happens if the wrong record is matched?

The analyst’s responsibility is not to eliminate all uncertainty.

The analyst’s responsibility is to expose uncertainty clearly.

---

# The Importance of Edge Cases

A workflow that only works in perfect conditions is not production-ready.

Analysts must actively search for:
- inconsistent naming,
- missing records,
- duplicate entries,
- invalid inputs,
- timing problems,
- permission issues,
- failed integrations,
- and unexpected user behavior.

## Questions to Ask

- What could go wrong?
- What happens if this field is blank?
- What happens if the folder does not exist?
- What happens if two records match?
- What happens if the user enters bad data?
- What happens if the process runs twice?
- What happens if the system cannot confidently determine the correct action?

---

# Analysts Translate Human Requests Into System Logic

Stakeholders speak in business language.

Systems operate on logic, rules, identifiers, workflows, and data.

The analyst sits between those two worlds.

Example stakeholder request:

> “Can we automatically move completed contracts into the correct folders?”

The analyst translates that into:

Input:
- completed contracts,
- document templates,
- resource IDs,
- target folder structure.

Process:
- identify document type,
- identify associated person,
- determine destination folder,
- prevent duplicate processing,
- log actions taken.

Output:
- file moved,
- audit trail recorded,
- destination linked to the correct record.

This translation work is the core value of requirements gathering.

---

# Good Analysts Think About Risk

Not every mistake has the same consequence.

A typo in a display label may be harmless.

Routing sensitive documents to the wrong folder may be severe.

Analysts should ask:
- What happens if this is wrong?
- Who is impacted?
- How likely is failure?
- How detectable is failure?
- How recoverable is failure?

Good requirements gathering balances:
- speed,
- certainty,
- operational risk,
- and implementation complexity.

---

# Documentation Exists To Communicate Thinking

Requirements documents are communication tools.

Their purpose is to help:
- developers,
- testers,
- stakeholders,
- support teams,
- and future analysts

understand:
- what problem is being solved,
- why the solution exists,
- how decisions are made,
- what assumptions exist,
- and where flexibility or uncertainty remains.

The document is evidence of analytical thinking.

It is not a replacement for analytical thinking.

---

# The Analyst’s Goal

The analyst’s job is not to produce perfect certainty.

The analyst’s job is to:
- reduce ambiguity,
- expose assumptions,
- identify risks,
- clarify logic,
- structure understanding,
- and define enough truth for the team to move forward responsibly.

The best analysts are not the people who complete templates the fastest.

They are the people who think most clearly about messy problems.