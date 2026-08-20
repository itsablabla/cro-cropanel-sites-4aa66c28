# Single-step funnel with dead end — dev spec
Site: example.com · Priority 2 · Urgent · Effort: Medium (2-5 days)

## Problem
The sole CTA exits to an external documentation site, leaving no in-page next step toward any conversion.

## Evidence (from the live site)
> The only call to action on the page is “Learn more”.
> Page copy reads “# Example Domain This domain is for use in documentation examples without needing permission. Avoid use in operations. [Learn more](https://iana.org/domains/example)”.

## Current state
h1: Example Domain; cta: Learn more (external link); notes: Single CTA leads away from site; no in-page next step.

## Required change
h1: Example Domain; cta: Primary in-page action (e.g., Sign up, Request demo); notes: Replace or supplement external link with a conversion-oriented CTA; keep external link as secondary.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Replace or supplement external link with a conversion-oriented CTA; keep external link as secondary.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_single_step_funnel_with_dead_end` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
