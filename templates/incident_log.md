# Incident Log -- [System Name]

One entry per incident. Keep it factual and time-stamped. For the
assessment you may fill in the template or add one simulated entry.

## Template
- Incident ID: [INC-001]
- Date / time (start): [YYYY-MM-DD HH:MM]
- Detected by: [name / alert]
- Severity: [Low | Medium | High | Critical]
- Summary: [what happened]
- Impact: [who / what was affected]
- Rollback trigger met: [yes/no -- which trigger]
- Actions taken: [ordered steps]
- Resolved (time): [YYYY-MM-DD HH:MM]
- Root cause: [short]
- Follow-up / post-incident: [issue link, fix, prevention]

## Example entry (simulated)
- Incident ID: INC-001
- Date / time (start): [YYYY-MM-DD HH:MM]
- Detected by: health-check alert
- Severity: High
- Summary: /health returned 500 after the vN deploy
- Impact: UI could not load data for about [6] min
- Rollback trigger met: yes -- /health failing twice in a row
- Actions taken: rolled back to vN-1; confirmed /health 200
- Resolved (time): [YYYY-MM-DD HH:MM]
- Root cause: missing env var in vN
- Follow-up: opened issue [#]; added env check to pre-flight
