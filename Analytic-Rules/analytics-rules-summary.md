# Analytics Rules Summary

## Rule 1 — Brute Force Failed Logins
- **Table:** SecurityEvent
- **Event ID:** 4625
- **MITRE:** T1110.001
- **Severity:** Medium
- **Schedule:** Every 5 min, lookback 10 min
- **Threshold:** Results > 0
- **Entity Mapping:** Account → TargetAccount, IP → IpAddress

## Rule 2 — Encoded PowerShell Execution
- **Table:** SecurityEvent (Sysmon)
- **MITRE:** T1059.001
- **Severity:** Medium
- **Schedule:** Every 5 min, lookback 1 hour
- **Threshold:** Results > 0
- **Entity Mapping:** Account → Account, Host → Computer

## Rule 3 — Suspicious User Account Created
- **Table:** SecurityEvent
- **Event ID:** 4720, 4732
- **MITRE:** T1136.001
- **Severity:** High
- **Schedule:** Every 5 min, lookback 1 hour
- **Threshold:** Results > 0
- **Entity Mapping:** Account → TargetAccount, Host → Computer


