# 🧪 Final Group Test Report Template — Word Puzzle Game Plus

**Level:** Intermediate QA | **Week 5:** Test Management

**Course:** Software Testing & Quality Assurance  
**Module:** Test Management (Week 5)  
**Project Type:** Group Assessment  
**Submission Date:** 2025-10-28

## Team Information

| Role | Name | Responsibilities |
|------|------|------------------|
| Test Manager | [Evans Nyamu] | Planning, scheduling, coordination, metric tracking |
| Risk Analyst |  | Risk identification, prioritization, test design linkage |
| Test Executor |  | Execution, evidence capture, defect logging |

## Test Executor Report

### Execution Results

Total: 8 test cases | Pass: 6 (75%) | Fail: 2 (25%)

### Test Cases

TC01: Answer Validation ✅  
Risk: TS-1 | Priority: High  
Got word "vascjaript" → typed "javascript" → showed "Correct! +10 points". Score went 0→10. Works good.

TC02: Leaderboard Saves ✅  
Risk: TS-3 | Priority: Critical  
Solved 3 words, got 30 points. Leaderboard showed "30 🥇". Hit F5 refresh → leaderboard still shows 30. localStorage working!  
Checked DevTools → found localStorage['leaderboard'] = "[30]". Good.


TC03: Shuffle Button ❌
Risk: TS-4 | Priority: Medium
Looked for the "Shuffle" button to rearrange the current puzzle letters. Can't find it anywhere! Only see: Submit, Hint, New Puzzle, Reset.

TC04: Hint Behavior ✅
Risk: TS-5 | Priority: Low
The score was 10. Clicked Hint once → lost 2 points (now 8), saw hint text "Step-by-step recipe to solve a problem". Clicked Hint again → got message "You've already used your hint for this puzzle!". Score stayed at 8. Fixed properly!

TC05: Reset Game ❌
Risk: TS-6 | Priority: Medium
Had a score of 15, solved 2 puzzles. Clicked Reset → score went to 0, solved count to 0. However, the puzzle word stayed the same ("mrkewafor") and didn't load a new one. Had to click "New Puzzle" manually.
Bug: Reset doesn't clear the current puzzle display.
Defect: Issue #1

TC06: Mobile View ❌
Risk: TS-7 | Priority: High
Opened DevTools, switched to Galaxy S21 (360×800). Buttons are wrapped okay, but the input box is super narrow. In landscape mode, the "Bonus at" counter disappeared off the edge.
Bug: Layout is cramped on small phones.
Defect: Issue #3

TC07: Wrong Answer (Negative) ✅
Priority: Medium
Word was "debugging", typed "random" → got "Incorrect, try again!" message. Score didn't change. Good error handling.

TC08: Empty Input (Negative) ✅
Priority: Medium
Left input blank, clicked Submit → got "Please enter a guess!" message. Nothing broke. Good validation.

TC09: Bonus Round ✅
Priority: High
Solved 3 puzzles in a row (got 10, 10, 10). After 3rd → saw "🎉 Bonus Round! Score doubled!" Score jumped from 30 to 60. Counter reset to "Bonus at: 3". Bonus math correct!


## Test Cases

| ID | Feature | Objective | Expected Result | Actual Result | Status | Risk Link |
|----|---------|-----------|----------------|---------------|--------|-----------|
| TC01 | Answer Validation | Verify correct answers are accepted | Display “Correct”, add +10 points | Correct accepted; score updated 0→10 | Pass | TS-1 |
| TC02 | Leaderboard Saves | Verify leaderboard persists across refresh | Score saved & shown after refresh | localStorage preserved ([30]) | Pass | TS-3 |
| TC03 | Shuffle Button | Allow reshuffle of current puzzle | Letters reshuffle in-place | No Shuffle button present | Fail | TS-4 |
| TC04 | Hint Behavior | Hint deducts points only once | −2 points on first hint; subsequent hint blocked | Behavior as expected | Pass | TS-5 |
| TC05 | Reset Game | Reset clears score and loads new puzzle | Score→0, solved→0, new puzzle displayed | Score/solved reset but puzzle remained | Fail | TS-6 |
| TC06 | Mobile View | Game usable on small screens | UI elements visible & usable on Galaxy S21 | Input narrow; bonus counter cut off | Fail (UI) | TS-7 |
| TC07 | Wrong Answer (Negative) | Incorrect answer shows error | Show "Incorrect, try again!" & no score change | Works as expected | Pass | TS-1 |
| TC08 | Empty Input (Negative) | Empty submit is validated | Show "Please enter a guess!" & no error | Works as expected | Pass | TS-1 |
| TC09 | Bonus Round | Every 3 solves double score | After third solve, score doubled | Bonus triggered; score doubled 30→60 | Pass | TS-2 |


## Defects

| ID | Issue Title | Severity | Risk ID | Status | GitHub Link |
|----|-------------|----------|---------|--------|-------------|
| #1 | Reset Doesn't Clear Puzzle | Medium | TS-6 | Open | (link pending) |
| #2 | Shuffle Button Missing | High | TS-4 | Open | (link pending) |
| #3 | Mobile Layout Cramped | Medium | TS-7 | Open | (link pending) |

## Metrics

- Test Case Pass Percent: 75% (6/8 executed as reported)  
- Defect Density: 0.375 (3 defects ÷ 8 test cases)  
- Risk Coverage Percent: 75% (6 of 8 identified risks covered by executed tests)  
- Regression Success Rate: TBD (post-fix retest required)

### Defect Summary

- Total Defects Logged: 3  
- Critical / High: 1 (Issue #2 marked High / Critical risk)  
- Fix Rate: 0% (no fixes applied yet) — update after dev fixes and retest

## Test Control & Project Management

### Phases

| Phase | Deliverable | Actual Output | Variance | Owner |
|-------|-------------|---------------|----------|-------|
| Planning & Test Design | Test plan, prioritized risks & test-case list | Completed: Test plan and prioritized list created | 0 | Test Manager |
| Test Case Creation & Automation Setup | Test cases, automation skeleton | Completed: Test cases documented; automation recommended (Selenium/Appium) | 0 | Test Executor |
| Test Execution & Defect Triage | Execute tests, log defects, triage | Completed: 8 test cases executed; 3 defects logged and triaged | 0 | Test Executor / Test Manager |
| Report Finalization & Submission | Final report & submission | Planned: Finalize and submit report by 2025-10-28 AM | - | Test Manager |

**Progress Tracking Method:** Jira / Tello boards for task tracking; GitHub Issues for defects and PRs.  
**Change Control Notes:** Defects logged as Issues #1–#3; severity assigned and ready for dev fixes. Test Manager to approve fixes and schedule retest.

## Lessons Learned

- Most Defect Prone Feature: Reset / UI behaviors (Reset not fully clearing state; mobile layout issues).  
- Risk Analysis Impact: Prioritization correctly highlighted leaderboard and input/score risks; enabled focused test coverage.  
- Team Communication Effectiveness: Clear handover from Test Executor to Test Manager; include screenshots/evidence in GitHub Issues to speed triage.  
- Improvements for Next Cycle: Add Shuffle feature spec or remove from test matrix if not intended; add responsive CSS tests; automate smoke tests to catch regressions early.

## Attachments

- localStorage screenshot showing "[30]" (leaderboard persistence) — include when uploading evidence.  
- DevTools screenshots for mobile layout and input width.  
- Test execution logs (attach here or reference GitHub Issue attachments).

## Sign Off

| Name | Role | Initials | Date |
|------|------|-----------|------|
| Evans Nyamu | Test Manager | EN | 2025-10-27 |
|  | Risk Analyst |  |  |
|  | Test Executor |  |  |

## Overall Summary

**Statement:** The Word Puzzle Game Plus shows solid core functionality: answer validation, hint behavior, leaderboard persistence, and bonus-round math are working as expected. Three defects were found (Reset not loading a new puzzle, missing Shuffle button, and mobile layout issues). The current execution produced a 75% pass rate.  

**Test Status:** ☐ Completed / ☑ In Progress / ☐ Deferred  
-- Remaining: implement fixes for Issues #1–#3, retest affected cases (TC03, TC05, TC06), and update metrics after retest.
2. Toggle device mode, pick Galaxy S21 (360×800)  
3. Try using a game  
Expected: Everything readable and usable  
Actual: Input field squished, bonus counter cuts off in landscape  
Impact: Hard to use on small phones. Not terrible, but annoying.  
Note: Works okay on bigger screens. Just tiny phones struggle.

### Metrics

| Metric | Value | Formula / Notes |
|--------|-------|-----------------|
| Pass Rate | 75% (6/8) | 6 passed out of 8 total test cases (as executed) |
| Defect Density | 0.375 (3 ÷ 8) | 3 defects over 8 test cases |
| Risk Coverage | 75% (6/8 risks) | 6 of 8 identified risks covered by executed tests |

### Untested Risks

- TS-2: Score math bugs (didn't find any wrong calculations)  
- TS-8: Performance lag (game ran smoothly, no lag noticed)

### What I Found

Good stuff:  
- Bonus round math is accurate (×2 every 3 solves)  
- Leaderboard saves properly to localStorage  
- Hint only works once per puzzle now  
- Enter key works for submitting

Needs fix:  
- Reset should auto-load the new puzzle  
- Mobile spacing could be better

Exit Status: 75% pass rate. Not bad, but the Reset bug should be fixed before launch.

### Notes for Test Manager

Done:  
- All 8 cases tested  
- 3 bugs logged with steps  
- Checked bonus round manually (works!)  
- Metrics calculated  

Handover:  
- Fix Issue #1 (Reset doesn't load new puzzle - medium priority)  
- Fix Issue #2 (Shuffle button missing - high priority)  
- Fix Issue #3 (Mobile layout cramped - medium priority)  
- Retest TC03, TC05, and TC06 after dev fixes  

Time spent: About 3 hours total

###
- 
 - Verify functional correctness of the core game features (puzzle scramble, guess evaluation, hint behavior, scoring, bonus round, reset).
 - Validate persistence and ordering of the leaderboard across sessions (top-3 behavior in localStorage).
 - Execute risk-based test cases (functional, negative, and usability) and log defects with reproduction evidence.
 - Produce test metrics (Test Case Pass %, Defect Density, Risk Coverage, Regression Success Rate) and deliver final report by 2025-10-28.
### Scope

**In Scope:**
- 

**In Scope:**
- Functional testing of core features: New Puzzle, Submit Guess, Hint, Reset Game, Score calculation and Bonus Round.
- Leaderboard behavior and persistence in `localStorage` (top-3 ordering, save/load across refreshes).
- Risk-based test cases (minimum 8 test cases including ≥2 negative and ≥1 usability test).
- Accessibility basics (keyboard Enter to submit, ARIA labels present) and desktop Chrome compatibility.
- Automation: implement smoke automation for critical flows using Selenium (web) and Appium for any mobile responsive verification.

**Out of Scope:**
- Backend or server-side integrations (there is no server component in the current app).
- Multi-user or networked leaderboard (concurrent sessions, server-side ranking).
- Cross-browser exhaustive testing beyond Chrome (full cross-browser matrix may be deferred to future cycles).
- Major refactors of game logic or UI redesigns — only small, low-risk bug fixes recommended.

**Out of Scope:**
- 

### Tools & Resources
- Project management / Task tracking:
	- Jira (issue tracking, sprint boards, backlog, defects)
	- Tello (project/task boards)  
- Test automation tools:
	- Selenium (Web automation for browser-based tests)
	- Appium (Mobile automation for Android/iOS)
- Code & issue repository:
	- GitHub (repository, Issues for defect tracking, PRs)
- Browsers / Devices:
	- Chrome (Desktop testing)
	- Android emulator / iOS simulator (mobile testing)
- Automation runtime & tooling:
	- Node.js / npm (test runners, WebDriver bindings)
	- Language bindings for Selenium/Appium as needed (e.g., JavaScript, Python, Java)
- Continuous Integration (recommended):
	- GitHub Actions (run automation on push / PR)

### Test Manager — Suggested Activities

- Maintain the master test schedule (milestones, deadlines, owners) in Jira/Tello.
- Create and assign test execution tasks and test-case ownership in the project board.
- Coordinate daily/weekly defect triage; ensure each defect has severity, reproduction steps, and screenshots.
- Track and publish metrics (see Metrics section): Test Case Pass %, Defect Density, Risk Coverage, Regression Success Rate.
- Approve environment readiness (browsers, emulators, devices) and mark entry/exit criteria for test phases.
- Produce weekly status reports and final sign-off when exit criteria are met.

- 

### Schedule

| Phase | Planned Duration | Actual Duration | Status |
|-------|------------------|-----------------|--------|
| Planning & Test Design | Sat 2025-10-25 (same day) — 1 day |  | Planned |
| Test Case Creation & Automation Setup | Sun 2025-10-26 — 1 day |  | Planned |
| Test Execution & Defect Triage | Mon 2025-10-27 — 1 day |  | Planned |
| Report Finalization & Submission | Tue 2025-10-28 — morning (deadline) |  | Planned |

Notes / Owner assignments:
- Test Manager (you): maintain schedule, coordinate owners, run daily triage, and approve sign-off (Owner: Test Manager).
- Risk Analyst: prepare risk-prioritized test cases by end of Planning day (Owner: Risk Analyst).
- Test Executor(s): create test data and execute test cases and automation scripts (Owners: Test Executor(s)).

Critical milestones:
- 2025-10-25 EOD: Test plan and prioritized test case list ready.
- 2025-10-26 EOD: Automation smoke tests ready and test cases implemented.
- 2025-10-27 EOD: All test cases executed; defects logged and triaged; metrics updated.
- 2025-10-28 AM: Final report (`Group_Test_Management_Report.md`) completed and submitted.

## Risk Analysis
## Word Puzzle Plus - Risk Analyst

### Risk Register

| Risk ID | Feature | Description | Probability | Impact | Severity | Note |
|---------|---------|-------------|-------------|--------|----------|------|
| TS-1 | Input Field | Correct answer typed but marked wrong | Medium | High | High | Input validation issue |
| TS-2 | Score System | Points not added correctly | Medium | High | High | Logic bug in score |
| TS-3 | Leaderboard | Scores lost after page refresh | High | High | Critical | Data not saved locally |
| TS-4 | Shuffle Button | Doesn’t reshuffle puzzle | Medium | Medium | Medium | JS event listener failure |
| TS-5 | Hint Button | Deducts point even if not used | Medium | Medium | Medium | Misplaced function trigger |
| TS-6 | Reset Button | Doesn’t clear puzzle but reset score | Medium | Medium | Medium | UI not fully resetting |
| TS-7 | Layout | Button overlap in mobile view | Medium | High | High | Poor responsive design |
| TS-8 | Performance | Game lags after long play | Low | Medium | Low | Memory leak or timer issue |

### Risk Prioritization

Notes: For prioritization we map Probability / Impact to numeric values (Low=1, Medium=2, High=3) and compute Risk Score = Probability × Impact. This produces a sortable risk score for prioritization.

| ID | Probability (1-3) | Impact (1-3) | Risk Score (P×I) | Priority | Rank |
|----|-------------------:|------------:|-----------------:|----------|-----:|
| TS-3 | 3 | 3 | 9 | Critical | 1 |
| TS-1 | 2 | 3 | 6 | High | 2 |
| TS-2 | 2 | 3 | 6 | High | 3 |
| TS-7 | 2 | 3 | 6 | High | 4 |
| TS-4 | 2 | 2 | 4 | Medium | 5 |
| TS-5 | 2 | 2 | 4 | Medium | 6 |
| TS-6 | 2 | 2 | 4 | Medium | 7 |
| TS-8 | 1 | 2 | 2 | Low | 8 |

### High-Risk Test Cases

| Test case ID | Title | Steps | Expected Result | Related Risk | Priority |
|--------------|-------|-------|-----------------|--------------|----------|
| TC01 | Correct Answer | Enter ‘Algorithm’ and Press Submit | Display “Correct”, adds +10 points | TS-1 | High |
| TC02 | Score Persistence | Get a score, refresh page | Score still appears on leaderboard | TS-3 | Critical |
| TC03 | Shuffle Button | Click Shuffle 3 times | Word letters rearrange each time | TS-4 | Medium |
| TC04 | Hint Deduction | Request hint once | Deducts −2 points only once | TS-5 | Low |
| TC05 | Reset Button | Start game and press Reset | Score resets, new puzzle loads | TS-6 | Medium |
| TC06 | Mobile Layout | Open in phone view | Buttons visible & clickable | TS-7 | High |


## Test Cases

| ID | Feature | Objective | Expected Result | Actual Result | Status | Risk Link |
|----|---------|-----------|----------------|---------------|--------|-----------|
| | | | | | | |

## Defects

| ID | Issue Title | Severity | Risk ID | Status | GitHub Link |
|----|-------------|----------|---------|--------|-------------|
| | | | | | |

## Metrics

- Test Case Pass Percent: 
- Defect Density: 
- Risk Coverage Percent: 
- Regression Success Rate: 

### Defect Summary

- Total Defects Logged: 
- Critical High: 
- Fix Rate: 

## Test Control & Project Management

### Phases

| Phase | Deliverable | Actual Output | Variance | Owner |
|-------|-------------|---------------|----------|-------|
| | | | | |

**Progress Tracking Method:**  
**Change Control Notes:**

## Lessons Learned

- Most Defect Prone Feature: 
- Risk Analysis Impact: 
- Team Communication Effectiveness: 
- Improvements for Next Cycle: 

## Attachments

- 

## Sign Off

| Name | Role | Initials | Date |
|------|------|-----------|------|
| | Test Manager | | |
| | Risk Analyst | | |
| | Test Executor | | |

## Overall Summary

**Statement:** 

**Test Status:** ☐ Completed / ☐ In Progress / ☐ Deferred
