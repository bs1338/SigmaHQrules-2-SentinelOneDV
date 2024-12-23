# proc_creation_win_whoami_parent_anomaly

## Title
Whoami.EXE Execution Anomaly

## ID
8de1cbe8-d6f5-496d-8237-5f44a721c7a0

## Author
Florian Roth (Nextron Systems)

## Date
2021-08-12

## Tags
attack.discovery, attack.t1033, car.2016-03-001

## Description
Detects the execution of whoami.exe with suspicious parent processes.

## References
https://brica.de/alerts/alert/public/1247926/agent-tesla-keylogger-delivered-inside-a-power-iso-daa-archive/
https://app.any.run/tasks/7eaba74e-c1ea-400f-9c17-5e30eee89906/
https://www.youtube.com/watch?v=DsJ9ByX84o4&t=6s

## False Positives
Admin activity
Scripts and administrative tools used in the monitored environment
Monitoring activity

## SentinelOne Query
```
EventType = "Process Creation" AND (EndpointOS = "windows" AND (TgtProcImagePath endswithCIS "\whoami.exe" AND (NOT ((SrcProcImagePath endswithCIS "\cmd.exe" OR SrcProcImagePath endswithCIS "\powershell_ise.exe" OR SrcProcImagePath endswithCIS "\powershell.exe" OR SrcProcImagePath endswithCIS "\pwsh.exe") OR SrcProcImagePath = "" OR SrcProcImagePath IS NOT EMPTY)) AND (NOT SrcProcImagePath endswithCIS ":\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe")))

```