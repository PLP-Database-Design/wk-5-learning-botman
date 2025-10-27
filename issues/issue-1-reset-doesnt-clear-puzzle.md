# Issue #1 — Reset Doesn't Clear Puzzle

**Severity:** Medium
**Risk ID:** TS-6
**Reported by:** Test Executor
**Status:** Draft

## Summary
When the user clicks the Reset button the score and solved count reset to 0, but the scrambled word display remains unchanged. The UI shows "Game reset!" but the puzzle does not refresh.

## Steps to Reproduce
1. Play the game and solve 1–2 puzzles so score > 0.
2. Observe the current scrambled word.
3. Click the "Reset" button.

## Expected Result
- Score resets to 0.
- Solved count resets to 0.
- A new puzzle is loaded and displayed (or the current puzzle is cleared and a new one appears automatically).

## Actual Result
- Score and solved count are reset to 0.
- The scrambled word display remains the same (old puzzle still visible).
- User must click "New Puzzle" manually to get a new puzzle.

## Impact
Confusing UX: user thinks the game has reset but the visible puzzle is still the old one.

## Notes / Root-cause (observed)
The code sets `scrambledWordEl.textContent = ""` but does not call `newPuzzle()` in the `resetGame()` function. A low-risk code change to call `newPuzzle()` at the end of `resetGame()` should fix the issue.

## Suggested Fix
In `resetGame()` call `newPuzzle()` after clearing state (or explicitly load a new puzzle). Add a small delay if you want to show the "Game reset!" message briefly before the new puzzle appears.

## Attachments
- (add screenshot showing old puzzle after reset)

## Labels
- bug, medium-priority, ui

## Assignee
- (assign developer)
