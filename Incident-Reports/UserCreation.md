# IR-003 — Suspicious Local User Account Created
**Date:** 2026-05-24
**Severity:** High
**Status:** Resolved (Lab)

## What Happened
A new local user account named "hacker" was created on the Windows 
victim machine and immediately added to the local Administrators group. 
This simulates a common post-exploitation technique where attackers 
create backdoor accounts for persistent access.

## How It Was Detected
Sentinel Analytics Rule fired on Event ID 4720 (user account created) 
and Event ID 4732 (user added to privileged group) within the same 
timeframe from the same host.

## Attack Details
| Field | Value |
|-------|-------|
| MITRE Technique | T1136.001 |
| Tactic | Persistence |
| New Account | hacker |
| Added To Group | Administrators |
| Target Host | Windows VM |
| Created By | labuser (simulated compromised account) |



## What I Learned
Monitoring both 4720 and 4732 together is important — account creation 
alone could be legitimate, but creation followed immediately by 
addition to Administrators is a strong signal of malicious intent. 
Combining both Event IDs in one rule reduces false positives.

## Recommended Response
1. Immediately disable the newly created account
2. Remove account from Administrators group
3. Identify which account created it and treat as compromised
4. Review all activity from the creating account in last 24 hours
5. Check for other persistence mechanisms on the same host
6. Reset credentials for all accounts on the affected machine