# Maintenance Requests System PRD

# 1. Problem

The maintenance company currently handles maintenance requests through phone calls and manual coordination. Requests can be forgotten, technicians may be double-booked, and management lacks visibility into request status and technician workload. The goal of the system is to centralize request intake, technician assignment, request completion, and operational reporting.

# 2. Users

## Dispatcher

Enter customer requests and assign technicians efficiently.

## Technician

View assigned requests on a mobile application and close requests with a maintenance report.

## Manager

Monitor operational performance, technician workloads, and request statistics.

# 3. Measurable Goals

- Assign a technician within 2 minutes of request creation.
- Ensure zero unassigned requests older than 24 hours.
- Reduce technician scheduling conflicts to zero.
- Allow technicians to close requests from the mobile application in less than 3 minutes.
- Provide daily statistics for management.

# 4. Features

## Story 1

As a dispatcher, I want to create a maintenance request, so that customer issues can be tracked and assigned.

### Acceptance Criteria

- A request cannot be created without a customer name.
- A request cannot be created without a description.
- A priority (normal or urgent) must be selected.
- After creation, the request status becomes `new`.

## Story 2

As a dispatcher, I want to assign a technician to a request, so that the visit can be scheduled.

### Acceptance Criteria

- I can only assign technicians who are available at the selected time.
- After assignment, the request status becomes `assigned`.
- I cannot assign a technician to a cancelled request.
- I cannot assign a technician to a completed request.

## Story 3

As a dispatcher, I want to cancel an unassigned request, so that invalid requests do not waste technician time.

### Acceptance Criteria

- Cancellation is allowed only when the request is in `new` status.
- Assigned requests cannot be cancelled.
- Cancelled requests have status `cancelled`.
- The cancellation is recorded with a timestamp.

## Story 4

As a technician, I want to see all requests assigned to me, so that I can plan my work.

### Acceptance Criteria

- The technician can only see requests assigned to them.
- Requests are sorted by scheduled visit time.
- New assignments appear in the mobile application.
- Cancelled requests are clearly marked.

## Story 5

As a technician, I want to start work on an assigned request, so that the dispatcher can see that the visit is in progress.

### Acceptance Criteria

- Only the assigned technician can start work.
- Starting work changes the request status to `in_progress`.
- A cancelled request cannot be started.
- A completed request cannot be started.

## Story 6

As a technician, I want to close a request with a report, so that completed work is recorded.

### Acceptance Criteria

- A report is required before closing the request.
- Closing a request changes the status to `done`.
- The completion timestamp is recorded automatically.
- The report remains visible after the request is completed.

## Story 7

As a manager, I want to see the number of open requests, so that I can monitor operational workload.

### Acceptance Criteria

- The dashboard shows the number of requests in `new`, `assigned`, and `in_progress` status.
- The statistics update when request statuses change.
- Closed requests are not counted as open requests.

## Story 8

As a manager, I want to see technician workload statistics, so that work can be distributed fairly.

### Acceptance Criteria

- The system shows the number of active requests assigned to each technician.
- The system shows the number of completed requests per technician.
- Technicians with no assigned requests are included in the report.
- Statistics can be viewed for the current day.

# 5. Out of Scope

The following features are not included in the first release:

- Online payment processing
- Customer self-service mobile application
- SMS notifications
- PDF report generation
- ERP integration
- Technician GPS tracking

# 6. Technical Constraints

- Backend: Laravel
- Web frontend: Next.js
- Mobile application: Flutter
- Authentication: Sanctum
- Database: MySQL
- Technician devices: Android phones
- Languages: Arabic and English
- Approximately 8 technicians
- Approximately 30 requests per day
- Customers submit requests by phone and the dispatcher enters them into the system

# 7. Open Questions

- Can a technician reject an assigned request?
- Can a request be reassigned after work has started?
- Should urgent requests bypass normal scheduling rules?
- Should managers be able to manually edit technician reports?
- How long should completed requests be retained?

# 8. Adversarial Review

## Findings

1. The original goals did not clearly define assignment and closure targets.
2. Some stories did not explicitly prevent invalid state transitions.
3. Reporting requirements were initially too vague.
4. Request cancellation rules required clarification.

## Changes Made

1. Added measurable goals for assignment time and unassigned requests.
2. Added acceptance criteria preventing assignment to completed and cancelled requests.
3. Added specific workload reporting criteria for managers.
4. Clarified that cancellation is only allowed before assignment.

## Review Outcome

After the adversarial review:

- Added measurable goals for assignment and closure times.
- Added validation rules for invalid status transitions.
- Clarified cancellation behaviour.
- Improved manager reporting requirements.
