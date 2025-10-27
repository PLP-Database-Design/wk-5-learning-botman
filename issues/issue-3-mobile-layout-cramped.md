# Issue #3 — Mobile Layout Cramped

**Severity:** Medium
**Risk ID:** TS-7
**Reported by:** Test Executor
**Status:** Draft

## Summary
On small viewport sizes (e.g., Galaxy S21 360×800), the input box becomes very narrow and the "Bonus at" pill can be pushed off-screen in landscape orientation. Buttons wrap but the input and status UI become hard to use.

## Steps to Reproduce
1. Open the app in Chrome.
2. Open DevTools (F12) → Toggle device toolbar → Select Galaxy S21 or set viewport to 360×800.
3. Switch orientation to landscape and try interacting with the input and controls.

## Expected Result
- UI components scale/stack sensibly for narrow widths: input remains usable, controls accessible, and status pill visible.

## Actual Result
- Input field is very narrow (hard to type).  
- "Bonus at" status pill can be clipped / pushed off-screen in landscape.

## Impact
Poor usability on small mobile devices; users may be unable to type guesses or see important status information.

## Notes / Root-cause (observed)
The layout grid uses fixed paddings and a grid with two columns; responsive rules exist but further CSS tweaks are needed for small widths (flex adjustments, wider input min-width, allow overflow/wrapping for the status pill).

## Suggested Fix
- Increase input min-width / allow it to grow via flex: `input[type="text"]{ min-width: 140px; flex-basis: 60%; }` for small breakpoints.  
- Ensure `.statusbar` and pill elements wrap gracefully (use `flex-wrap: wrap` and `min-width` constraints).  
- Test in a Galaxy S21 viewport in both portrait and landscape.

## Attachments
- DevTools screenshots (portrait & landscape)

## Labels
- bug, medium-priority, responsive

## Assignee
- (assign frontend developer)
