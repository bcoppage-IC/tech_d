# Release Plan -- [System Name]

System context: [API] + [DB] + [UI].

## 1. Pre-flight checklist
- [ ] All: API, database, and UI changes are reviewed, merged, and tagged 
- [ ] DB: Updates were tested in staging, work safely with the current API version, and won't break existing data.
- [ ] DB: A database backup was taken within the last hour and confirmed to work.
- [ ] DB: All required environment variables, keys, and feature flags are in place.
- [ ] UI:  Automated builds and tests passed with no critical security issues.
- [ ] All: Dashboards, logs, and alerts are turned on and working.
- [ ] All: The previous working version is saved and ready to restore immediately.

## 2. Release steps (in order)
1. Notify that release is starting and name the owner.
2. Ensure that database responds and compare to baseline (testing from pre-flight)
3. Update database.
4. Update SPI / test to see if it functions.
5. test API and database together.
6. Final pass on UI; have back-up, so that rollback to functioning version is available if needed.
7. Announce release date. Ensure that all relevent parties are represented.

## 3. Rollback
Rollback trigger (be specific -- what makes you roll back):
- [e.g. error rate > 2% for 5 min, OR /health failing twice in a row]

Rollback steps:
1. The Release Owner announces the rollback in the chat channel and stops further updates.
2. Switch off any feature flags tied to the new release.
3. Switch the frontend back to functining version.
4. Roll API servers back to functioning version
5. Leave safe, backward-compatible database updates in place. Only restore from the pre-release backup if the database change itself is causing outages and the Database Owner approves it.
6. Verify normal functioning.
7. Record what happened (incident report).


## 4. Monitoring signals
API: Server Health 
API: Server Errors (failed requests)
API: Response Speed (request speeds)
DB: Load & Connections 
UI: Uptime & Page Errors 


## 5. Roles and escalation
- Release owner: Freeda Garcia
- On-call: Raymond Hall
- Comms: Andrew Thomas
- Escalation path: on-call -> John -> Ben if not
  resolved in [15] min
