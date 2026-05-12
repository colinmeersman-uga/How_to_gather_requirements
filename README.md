# How to Gather Requirements

## Overview

Requirements gathering in the RevOps Agile development process is the practice of turning stakeholder needs into clear, testable, prioritized user stories. The goal is to deliver value quickly, refine iteratively, and adapt when requirements change.

This guide combines the company wiki's Agile/user-story approach with practical lessons from a real requirements-gathering call about automating the routing of completed DocuSign/1099 contracts from a shared intake folder into the correct person-specific folders.

The key lesson: requirements gathering is not order-taking. It is structured discovery. A vague request such as "Can we automate this?" should become a set of user stories, acceptance criteria, edge cases, priorities, and follow-up actions.

---

## Purpose

The purpose of requirements gathering is to provide a clear and concise description of desired functionality from the end user's perspective.

Good requirements should help product owners, developers, testers, and stakeholders understand:

- who needs the change
- what action or capability they need
- why it matters
- how success will be tested
- how much effort may be required
- where the work belongs in the backlog
- what open questions, assumptions, or risks remain

---

## Scope

This guide applies to requirements gathering for:

- internal RevOps automations
- Salesforce, Box, DocuSign, and integration work
- process improvements
- reporting features
- operational workflows
- backlog refinement and sprint planning
- stakeholder discovery calls

It is intended for product owners, developers, testers, analysts, RevOps team members, and stakeholders who participate in product or process development.

---

## Core Components

### User Story

Use the standard format:

> As a [type of user], I want [an action] so that [a benefit or value].

Example:

> As a RevOps team member, I want completed 1099 contracts to be routed to the correct person-specific folder so that we do not rely on manual sorting.

### User Role or Persona

A user role identifies who needs the functionality. A persona provides more context about that user's goals, responsibilities, and pain points.

Examples:

- RevOps team member
- project manager
- sales operations user
- Salesforce admin
- implementation owner
- stakeholder reviewing completed work

### User Need

A short explanation of the problem the user is trying to solve.

Example:

> RevOps needs completed contract files to be organized without manual review of every item in a shared intake folder.

### Acceptance Criteria

Specific, testable conditions that must be true for the story to be considered complete.

Example:

- Given a completed 1099 contract arrives in the intake folder, when the automation identifies the person associated with the contract, then it moves the file to that person's target folder.
- Given a document does not match a supported template, when the automation reviews it, then the document is left unprocessed and logged for review.
- Given the target folder cannot be found, when routing is attempted, then the file is not moved and an exception is logged.

### Story Points

A relative estimate of effort, complexity, and uncertainty. Story points should be estimated collaboratively with the development team.

### Priority

The business ranking of the user story. Prioritize based on value, urgency, dependencies, risk reduction, and team capacity.

### Backlog

A prioritized list of user stories waiting to be refined, planned, built, tested, and reviewed.

---

## Requirements-Gathering Workflow

### Step 1: Identify User Roles

Start by identifying who the users are and who is affected by the process.

Ask:

- Who performs the process today?
- Who receives the output?
- Who is responsible if something goes wrong?
- Who validates that the solution works?

Deliverable:

- list of user roles or personas
- stakeholder list
- owner for validation

Example:

- RevOps team member who manages contractor onboarding
- Salesforce admin who maintains resource records
- automation owner who monitors routing failures
- stakeholder who needs to find completed contracts later

---

### Step 2: Understand User Needs

Gather information about what users need and what problems they face. Use interviews, discovery calls, process walkthroughs, surveys, examples, and existing tickets.

Ask:

- What happens today?
- What is manual, slow, unclear, or risky?
- What value should the solution deliver?
- What does success look like?

Case study lesson:

The initial ask was about automating file movement. The real need was to prevent completed contracts from piling up in a catch-all folder and to make the documents easy to find later.

Deliverable:

- problem statement
- desired outcome
- current workflow summary
- pain points

---

### Step 3: Map the Current Workflow and Systems

Before writing stories, understand the process across systems.

Ask:

- Which system creates the item?
- Which system stores it?
- Which system contains the source-of-truth data?
- Which system should be updated?
- Are there permissions or access gaps?

Example system map:

| System | Role in Workflow |
| --- | --- |
| DocuSign | Delivers completed documents |
| Box | Stores intake and destination folders |
| Salesforce | Stores resource/person data and related record IDs |
| Automation layer | Reads, classifies, routes, and logs documents |

Case study lesson:

Do not assume the solution belongs in the system where the request originated. In the call, the request touched Salesforce and DocuSign, but the core automation was about routing files in Box.

Deliverable:

- current-state workflow
- target-state workflow
- system ownership notes
- permissions/access needs

---

### Step 4: Write User Stories

Use the standard user story format:

> As a [type of user], I want [an action] so that [a benefit or value].

Write from the user's perspective. Avoid technical implementation detail unless it is necessary for clarity.

Weak story:

> Automate DocuSign folder movement.

Better story:

> As a RevOps team member, I want completed 1099 contracts to be automatically routed to the correct person-specific folder so that the team does not rely on manual sorting.

Strong supporting story:

> As a Salesforce user, I want the resource record to show where the completed contract is stored so that I can confirm receipt and locate the file when needed.

Deliverable:

- draft user stories
- user role
- user need
- business value

---

### Step 5: Define Acceptance Criteria

Acceptance criteria describe the specific, testable conditions that make the story complete.

Use plain language. Acceptance criteria should be clear enough for a tester, developer, and stakeholder to agree whether the story passes.

Helpful format:

> Given [context], when [action], then [expected result].

Ask:

- What must happen for this story to be complete?
- What should happen when the normal path works?
- What should happen when something fails?
- What should be logged or visible afterward?

Example acceptance criteria:

- Given a completed 1099 contract arrives in the intake folder, when the document matches an approved template and contains a valid resource identifier, then the file is moved to the matching person-specific folder.
- Given the document cannot be matched to a known person, when the automation processes the file, then the file remains in the intake folder and an exception is logged.
- Given a file is moved, when the move succeeds, then an audit entry records the source folder, destination folder, document type, matched person, timestamp, and rule used.

Deliverable:

- testable acceptance criteria
- exception handling requirements
- audit/logging requirements

---

### Step 6: Estimate Story Points

Collaborate with the development team to estimate the effort required.

Consider:

- technical complexity
- number of systems involved
- data quality risk
- exception handling
- unknowns
- testing effort
- dependencies

Example:

| Story | Initial Estimate |
| --- | --- |
| Route known contract types to existing folders | 5 points |
| Add audit trail for routed documents | 3 points |
| Update Salesforce record with Box link | 5 points |
| Build unmatched-document review queue | 8 points |

Deliverable:

- point estimate for each story
- notes on assumptions and uncertainty

---

### Step 7: Prioritize User Stories

Add stories to the backlog and prioritize them based on user value, dependencies, and risk.

Ask:

- Which story delivers the most immediate value?
- Which story reduces the biggest manual pain point?
- Which stories are prerequisites for others?
- Which risks should be tested early?

Example priority order:

1. Route known 1099 contracts to existing person folders.
2. Log all routing actions and failures.
3. Update Salesforce with completed contract location.
4. Add support for additional document types.
5. Add advanced review queue or notifications.

Deliverable:

- prioritized backlog
- dependency notes
- recommended MVP scope

---

### Step 8: Refine and Review

Regularly review user stories with stakeholders and the team to improve clarity, feasibility, and value.

Ask:

- Is the story still relevant?
- Is the user value clear?
- Are acceptance criteria testable?
- Are dependencies known?
- Are edge cases captured?
- Are there examples the team can test against?

Case study lesson:

The team improved the requirement by clarifying that routing should use the person associated with the resource record, not variable company names entered on the signature line.

Deliverable:

- refined user stories
- updated acceptance criteria
- clarified open questions
- examples attached to stories

---

### Step 9: Plan Sprints, Develop, and Test

Select stories for development based on priority and team capacity. During implementation, test against acceptance criteria.

Ask:

- Which stories are ready for the sprint?
- Does the team have access to the needed systems and examples?
- What test data is required?
- How will stakeholders validate the work?

Deliverable:

- sprint-ready stories
- test plan
- sample inputs and expected outputs
- validation owner

---

### Step 10: Review and Demo

Present completed work to stakeholders during sprint review or demo.

Ask:

- Did the story meet the acceptance criteria?
- Does the workflow solve the business problem?
- What feedback should become a new story?
- What should be changed, refined, or deprioritized?

Deliverable:

- stakeholder feedback
- demo notes
- accepted stories
- follow-up backlog items

---

## Best Practices

### Keep It Simple

Write user stories and acceptance criteria in plain language. Avoid technical jargon unless needed for precision.

### Focus on Value

Every story should explain why the user needs the capability.

### Collaborate

Include stakeholders, product owners, developers, testers, and system owners. Requirements improve when the people building, using, and supporting the workflow all participate.

### Iterate

Requirements are refined over time. Do not try to design a perfect solution before learning from real usage.

### Define Clear Acceptance Criteria

Each story should have testable conditions for completion.

### Identify the Source of Truth

When multiple systems or fields contain similar data, decide which one should be trusted.

Case study example:

A person name or resource record ID from Salesforce was more reliable than a company name typed into a signature block.

### Explore Exceptions Early

A complete requirement includes failure behavior.

Examples:

- no matching person found
- multiple people match
- target folder missing
- document is blank or incomplete
- file was already processed
- unsupported document type

### Capture Audit and Visibility Needs

Ask whether the system should record what happened, notify anyone, or update a related record.

Example audit fields:

- file name
- document type
- matched person or record
- source location
- destination location
- timestamp
- routing rule used
- success/failure status
- error message, if any

### Separate Confirmed Requirements from Open Questions

Do not let assumptions masquerade as decisions. Track unresolved questions clearly.

---

## ChatGPT Automation Support

ChatGPT can assist with requirements work when given a transcript, notes, tickets, or stakeholder input.

Useful tasks:

- generate initial user story drafts
- identify user roles and personas
- extract business needs and pain points
- propose acceptance criteria
- identify edge cases and open questions
- suggest backlog priority based on value and dependencies
- rewrite technical requests as user-centered stories
- summarize refinement decisions

Example prompt:

```text
Analyze this requirements-gathering transcript. Extract user roles, user needs, user stories, acceptance criteria, edge cases, source-of-truth decisions, open questions, dependencies, and follow-up actions. Format the output for backlog refinement.
```

Example prompt:

```text
Rewrite these requirements as Agile user stories using the format: As a [type of user], I want [an action] so that [a benefit]. Add testable acceptance criteria using Given/When/Then.
```

Example prompt:

```text
Review these user stories for clarity, user value, dependencies, missing acceptance criteria, and unhandled edge cases. Suggest refinements.
```

---

## Case Study: DocuSign/Box Contract Routing

See [`examples/docusign-1099-routing-user-story.md`](examples/docusign-1099-routing-user-story.md) for a complete example of converting a discovery conversation into backlog-ready user stories.

---

## Minimum Deliverable for a Good Requirements Summary

A completed requirements summary should include:

- user roles or personas
- user needs
- user stories
- acceptance criteria
- story points or sizing notes
- priority
- current workflow
- desired workflow
- systems involved
- source-of-truth decisions
- edge cases
- audit/logging needs
- open questions
- follow-up owners
- sprint or backlog recommendation

---

## Final Takeaway

A good requirements-gathering session moves from a broad request to a refined backlog.

The facilitator should help the team move from:

> Can we automate this?

To:

> Here are the user roles, user needs, user stories, acceptance criteria, source-of-truth rules, exceptions, audit needs, priorities, and follow-up actions required to build this safely.