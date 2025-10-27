# Issue #2 — Shuffle Button Missing

**Severity:** High
**Risk ID:** TS-4
**Reported by:** Test Executor
**Status:** Draft

## Summary
Test case expected a "Shuffle" button to reshuffle the current puzzle's letters in-place. The UI does not contain a Shuffle control — available controls are Submit, Hint, New Puzzle, and Reset.

## Steps to Reproduce
1. Open the Word Puzzle Game Plus in the browser.
2. Inspect the controls available next to the input field.
3. Look for a "Shuffle" or "Reshuffle" button to rearrange the letters of the current scrambled word.

## Expected Result
- There should be a Shuffle button that rearranges the letters of the current puzzle without loading a new word.

## Actual Result
- No Shuffle button exists. Users must click "New Puzzle" to get a different word; this replaces the puzzle rather than reshuffling the current letters.

## Impact
Functionality gap: users who want to reshuffle the current puzzle cannot do so. Test cases that assume a Shuffle action cannot be executed.

## Notes / Root-cause (observed)
Risk Analyst / test plan included tests for a Shuffle control (TS-4) but the feature appears to be absent or removed from the codebase. Clarify product intent: if Shuffle should exist, add the UI element and a handler (use the `scrambleWord()` function on the current word). If Shuffle is not intended, update the test plan to remove the Shuffle test.

## Suggested Fix
- Option A (implement): Add a Shuffle button to the UI that calls a new function to reshuffle the currently displayed `currentWord` and update the `scrambledWordEl` accordingly.
- Option B (testplan): Remove Shuffle-related test cases from the test matrix and update risk documentation.

## Attachments
- (screenshot of current UI showing available buttons)

## Labels
- bug, high-priority, feature-clarification

## Assignee
- (assign developer / product owner to clarify)
