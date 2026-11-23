# Incident Log -- Cascade (Medline Operations Problem Navigator)



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

## Entry (simulated)
- Incident ID: INC-001
- Date / time (start): 2026-11-23 10:15
- Detected by: Ben Coppage, post-deploy count check
- Severity: High
- Summary: After the v2 deploy, the detection run returned 31 Problems
  instead of the 28 in the baseline run (window 2026-08-21 to 2026-09-20).
- Impact: Duplicate Problems for the same sites. Incidents were split
  across misspelled location names. Problems could be routed to the
  wrong resolution party. No data was lost.
- Rollback trigger met: yes -- Problem count did not match the baseline run
- Actions taken:
  1. Stopped the v2 detection job.
  2. Rolled back to v1.
  3. Re-ran detect.py on the same data file.
  4. Confirmed 28 Problems, matching the baseline.
  5. Spot-checked the first 3 Problems against script counts. All matched.
- Resolved (time): 2026-11-23 10:40
- Root cause: location_map.csv was not included in the v2 build. The 27
  rows with location typos were not corrected on load.
- Follow-up / post-incident:
  - Opened issue #12: add location_map.csv to the build.
  - Added a pre-flight check: detect.py stops if location_map.csv is missing.
  - Added a post-deploy check: Problem count must match the baseline before release.