# Example: DocuSign / 1099 Contract Routing

This example shows how to convert a discovery conversation into wiki-aligned Agile requirements.

## Initial Request

Can completed 1099 contracts be automatically moved from a shared intake folder into the correct person-specific folder?

## Current State

- Completed DocuSign documents arrive in a shared catch-all folder.
- A person previously sorted documents manually.
- Without manual sorting, the folder becomes cluttered and documents are harder to find.
- The process touches DocuSign, Box, and Salesforce.

## Desired Future State

- The system identifies supported completed contract documents.
- The system identifies the relevant person using stable source-of-truth data.
- The system moves the document to the correct target folder.
- The system logs what happened.
- If useful, the related Salesforce record includes a reference to the stored document.

## User Roles

| Role | Need |
| --- | --- |
| RevOps team member | Avoid manually sorting completed contracts |
| Salesforce admin | Use stable resource data to avoid routing errors |
| Automation owner | Troubleshoot routing actions and failures |
| Salesforce user | Confirm whether a completed contract was received and where it is stored |

## User Stories

### US-001: Route completed contracts

As a RevOps team member, I want completed 1099 contracts to be routed to the correct person-specific folder so that the team does not rely on manual sorting.

Acceptance criteria:

- Given a completed 1099 contract arrives in the intake folder, when it matches a supported template and known person, then the file is moved to that person's folder.
- Given a document does not match a supported template, when the automation reviews it, then the file is not moved and the event is logged.
- Given the target folder cannot be found, when the automation attempts routing, then the file is not moved and an exception is logged.

Priority: High

Story points: TBD by development team

### US-002: Use stable source-of-truth data

As a Salesforce admin, I want routing to use controlled resource data so that the automation is not dependent on inconsistent signature-line company names.

Acceptance criteria:

- Given the contract includes a resource identifier or controlled person field, when the automation identifies the target person, then it uses that value before relying on free-text signature data.
- Given company name and person name conflict, when the automation routes the document, then the stable resource/person identifier is treated as the source of truth.
- Given no reliable identifier exists, when the automation reviews the file, then it does not guess and logs the file for human review.

Priority: High

Story points: TBD by development team

### US-003: Maintain an audit trail

As an automation owner, I want every routing action and failure to be logged so that incorrect routing can be investigated.

Acceptance criteria:

- Given a file is processed, when routing succeeds or fails, then the log records the source location, destination location if applicable, document type, matched person, timestamp, and result.
- Given a file has already been processed, when the automation runs again, then it does not duplicate the routing action and records that the file was previously handled.
- Given routing fails, when the error is logged, then the log includes enough detail for support review.

Priority: High

Story points: TBD by development team

### US-004: Make completed documents discoverable from Salesforce

As a Salesforce user, I want the resource record to show where the completed contract is stored so that I can confirm receipt and access the document if authorized.

Acceptance criteria:

- Given a completed contract is routed successfully, when the related resource record is updated, then it includes a link or reference to the Box file location.
- Given a user does not have permission to access the document, when they view the reference, then normal access controls still apply.
- Given the Salesforce update fails, when routing succeeds, then the routing action remains logged and the Salesforce update failure is flagged.

Priority: Medium

Story points: TBD by development team

## Edge Cases

| Scenario | Expected Behavior |
| --- | --- |
| Unsupported document type | Do not move; log as unsupported |
| Missing person identifier | Do not guess; log for human review |
| Multiple possible person matches | Do not route automatically unless confidence rules are defined |
| Missing target folder | Do not create automatically unless approved; log exception |
| Document already processed | Do not reprocess; log prior handling |
| Blank or incomplete document | Do not mark as complete; log for review |
| Company name differs from person record | Prefer stable person/resource identifier |

## Open Questions

- What target folder structure should be used?
- Who can provide Box access?
- Which document types are included in version one?
- Which phrases, fields, or template identifiers classify each document type?
- Should missing folders be created automatically or flagged for review?
- Should Salesforce be updated in version one or handled as a later story?

## Backlog Recommendation

1. Build routing for known contract types and existing folders.
2. Add audit logging for processed and skipped files.
3. Add stable resource/person identifier support.
4. Add Salesforce record update with Box file reference.
5. Add broader document type support.
6. Add optional review queue or notifications.

## Sprint Review Demo Plan

1. Show a supported 1099 contract entering the intake folder.
2. Show the automation identifying the document type and person.
3. Show the file moved to the correct target folder.
4. Show the audit/log output.
5. Show an unsupported or ambiguous file being skipped or sent to exception handling.

## Lessons for Future Sessions

- Start with the current workflow before designing the solution.
- Translate automation requests into user stories.
- Identify the source of truth early.
- Capture edge cases and failure behavior.
- Keep the first version practical and improve based on results.
- End with open questions, owners, and backlog-ready next steps.