# Case Study 01: Insider IP Exfiltration & Behavioral Baseline Deviation

Classification: Sanitized Methodology Demonstration | Domain: Host Forensics, Memory Triage & Behavioral Profiling
Tools Utilized: KAPE, Volatility 3, Autopsy, Wireshark

## 1. Executive Scenario

A mid-sized R&D firm suspected a senior engineer of exfiltrating proprietary source code prior to resigning for a competitor. Standard DLP (Data Loss Prevention) alerts showed zero large outbound transfers, and basic Windows Event Logs appeared clean. NYCTO Operations Group was engaged to conduct rapid host/memory triage and reconstruct the subject's behavioral timeline.

## 2. Technical Triage & Artifact Extraction


### A. Rapid Collection & Volatile Memory Analysis (KAPE + Volatility 3)

• Collection: Deployed a targeted KAPE triage package (!SANS_Triage) alongside a raw physical memory capture (WinPmem) to preserve volatile state prior to workstation shutdown.
• Memory Findings (Volatility 3):
 • windows.pslist & windows.cmdline revealed a short-lived powershell.exe execution spawned outside normal working hours (02:14 UTC), invoking Compress-Archive to stage files into C:\Users\Public\Libraries\cache_tmp.dat.
 • windows.netscan identified an active TLS session to an uncategorized cloud storage IP (185.x.x.x:443) originating from a portable, non-installed binary (rclone.exe) executed from an external volume.

### B. Disk & Persistence Reconstruction (Autopsy)

• USB & Volume Correlation: Registry hive analysis (SYSTEM\CurrentControlSet\Enum\USBSTOR and NTUSER.DAT\MountPoints2) confirmed a Kingston USB device (S/N: 4C530001...) was mounted 11 minutes prior to the PowerShell staging event.
• Anti-Forensics Detection: Inspection of $UsnJrnl and $MFT timestamps revealed deliberate timestomping (SetFileTime anomalies where $STANDARD_INFORMATION predated $FILE_NAME creation timestamps) and wevtutil cl Security execution to purge login records.

### C. Network Anomaly Verification (Wireshark)

• Packet capture analysis of the perimeter firewall tap confirmed low-and-slow HTTPS chunked uploads (~1.8 MB bursts every 90 seconds over 45 minutes), deliberately throttled to stay below the organization's 50 MB single-session DLP threshold.

## 3. Behavioral & Criminological Attribution

Technical artifacts establish what happened; behavioral profiling establishes intent, operational tempo, and attribution for legal counsel:
• Operational Tempo Shift: Analysis of 90 days of UserAssist and Prefetch execution logs established a strict baseline working window (08:30 – 17:15 local time, zero weekend logins). Over the 14 days following a denied promotion, activity shifted abruptly to 01:00 – 03:30 nocturnal bursts targeting repositories outside the subject's assigned project scope.
• Intent & Countermeasure Awareness: The combination of rate-limited exfiltration (<2 MB chunks), renamed staging archives (.dat extension in a system-adjacent directory), and targeted Security log clearing demonstrated premeditation and familiarity with internal SOC alerting thresholds—ruling out accidental synchronization or routine backup behavior.
• Psycholinguistic Indicators: Examination of internal messaging artifacts during the 30-day pre-resignation window revealed marked linguistic distancing (drop in first-person plural pronouns "we/our", rise in grievance framing and self-justifying rationalization).

## 4. Defensible Deliverables Provided to Counsel

1. Verified Chain-of-Custody Package: SHA-256 hashed triage containers sealed inside an encrypted VeraCrypt volume per ISO/IEC 27037 guidelines.
2. Master Super-Timeline: Minute-by-minute correlation merging filesystem ($MFT), registry, volatile memory, and network flow events.
3. Executive Behavioral & Attribution Brief: Non-jargon narrative translating technical indicators of premeditation into clear evidentiary findings for civil trade-secret litigation.

