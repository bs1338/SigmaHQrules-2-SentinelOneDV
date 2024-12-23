# file_delete_win_sysinternals_sdelete_file_deletion

## Title
File Deleted Via Sysinternals SDelete

## ID
6ddab845-b1b8-49c2-bbf7-1a11967f64bc

## Author
Roberto Rodriguez (Cyb3rWard0g), OTR (Open Threat Research)

## Date
2020-05-02

## Tags
attack.defense-evasion, attack.t1070.004

## Description
Detects the deletion of files by the Sysinternals SDelete utility. It looks for the common name pattern used to rename files.

## References
https://github.com/OTRF/detection-hackathon-apt29/issues/9
https://github.com/OTRF/ThreatHunter-Playbook/blob/2d4257f630f4c9770f78d0c1df059f891ffc3fec/docs/evals/apt29/detections/4.B.4_83D62033-105A-4A02-8B75-DAB52D8D51EC.md

## False Positives
Legitime usage of SDelete

## SentinelOne Query
```
EventType = "File Delete" AND (EndpointOS = "windows" AND ((TgtFilePath endswithCIS ".AAA" OR TgtFilePath endswithCIS ".ZZZ") AND (NOT TgtFilePath endswithCIS "\Wireshark\radius\dictionary.alcatel-lucent.aaa")))

```