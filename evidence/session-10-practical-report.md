# Session 10 — Practical Assessment Report

## Scenario
A simulated dataset contains three failed logons for account `alex`, a successful logon, and two process-creation events on host `WS-04`. The command line is unavailable in the supplied records.

## Learner answers and assessment
### Exercise 1 — Identify the pattern
**Answer:** B — Three failed logons, then success, followed by PowerShell process creation.  
**Result:** Correct.

### Exercise 2 — Choose the next step
**Answer:** B — Validate the successful logon and investigate the PowerShell process, command line, and surrounding activity.  
**Result:** Correct.

### Exercise 3 — Evidence vs hypothesis
**Learner assessment:** Three failed logons followed by success does not prove an attack. The analyst should investigate because a process was created after the successful login; validate logon, process/command line, account, IP, and whether the activity was expected. Escalate with documentation if the evidence warrants it.

**Result:** Correct. The answer distinguishes suspicion from proof and identifies relevant next steps.

### Exercise 4 — Identify a limitation
**Answer:** B — The process command line is missing.  
**Result:** Correct.

## Score
**4/4 — all practical exercises passed.**

## Analyst feedback
A process-creation record (for example, Event ID 4688) shows that a process was created; it does not by itself prove that a suspicious script completed or that the activity was malicious. Seek command-line and parent-process details where available and correlate additional telemetry.

## Limitations
This is a simulated scenario, not evidence from a live Windows endpoint. The Session 10 quiz remains pending until the learner submits answers.
