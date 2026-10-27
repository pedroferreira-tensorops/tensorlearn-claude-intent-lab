# Intent: results-ready notification

## Purpose
Reduce avoidable calls from patients asking whether results are ready (PRD N-17). Tell the patient that an update is available and send them to the existing authenticated portal.

## Scope
Use the existing portal result route. Notify only after a doctor has reviewed the result and it has been released; a finished lab upload is not enough. Prevent duplicate notifications for the same released result version and handle delivery failures without duplicate messages.

## Exclusions
Out of scope: portal redesign, appointment scheduling, clinical interpretation, notifying third parties and the separate patient dashboard. Messages and operational logs never contain a diagnosis, test name, result value or treatment; no attachments or public result links.

## Success conditions
Measure status-only calls separately from clinical questions against a baseline measured during discovery, and track delivery failures. No numerical target is approved yet; the superseded 90% figure is not a target.

## Open decisions
- Channel (SMS, email, portal push): product owner and privacy owner decide after the consent and delivery review.
- Notifying the referring doctor: clinical owner and privacy owner decide recipient authorization. Not approved.

```json
{
  "notifyWhen": ["doctor-reviewed", "released"],
  "messageMayInclude": ["update-available"],
  "inScope": ["existing-portal-route", "duplicate-prevention", "delivery-failure-handling"],
  "openDecisions": [
    {"topic": "channel", "owners": ["product", "privacy"]},
    {"topic": "referring-doctor-notification", "owners": ["clinical", "privacy"]}
  ],
  "successMeasures": ["status-only-calls", "delivery-failures"],
  "numericTarget": null
}
```
