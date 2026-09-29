# Day 04

## Before CLAUDE.md

Prompt:

"Add a PATCH /api/v1/requests/{id}/status endpoint to update a request's status."

Observed result:

- Validation was placed in the Controller.
- No dedicated Form Request was created.
- Business logic was mixed with HTTP logic.
- Response formatting did not clearly follow existing Resource conventions.

## After CLAUDE.md

Same prompt:

"Add a PATCH /api/v1/requests/{id}/status endpoint to update a request's status."

Observed result:

- A dedicated Form Request was created.
- Business logic was placed in an Action.
- Responses used Resources.
- Authorization followed Policy-based patterns.
- Naming matched the project conventions.

## Skill Test

Prompt:

"Create a Form Request for assigning a technician."

Observed result:

- Form Request naming followed project conventions.
- Validation was kept out of Controllers.
- An `authorize()` method was included.
- `rules()` contained the validation logic.
- `prepareForValidation()` was considered when input normalization was needed.

## Improvements Added

Based on mistakes observed during previous work:

- Added a rule requiring validation in Form Requests.
- Added a rule requiring business logic in Actions.
- Added a rule requiring a Feature test for every endpoint.
- Added a rule requiring Resources for API responses.

## Conclusion

Adding CLAUDE.md and the Form Request Skill improved consistency with the existing project architecture and reduced incorrect suggestions.
