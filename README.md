# Malicious-URL-Alert-Triage-Lab

## Objective
Investigate a high‑priority alert triggered by an employee attempting to access a blacklisted external URL, validate authenticity using threat intelligence checks, and determine whether escalation is required.

---

## Step 1 – Identify Highest Priority Alert
- Reviewed unassigned alerts in the SOC queue.  
- Found two medium alerts and one high alert.  
- Selected the **high alert** due to priority.

![Lab 2 Screenshot](https://raw.githubusercontent.com/danyl-infosec/Alert-Triage-Lab-2/refs/heads/main/Lab%202%20Screenshot%201.png)

---

## Step 2 – Assign & Update Status
- Assigned the alert to myself.  
- Changed status from **“Awaiting Action” → “In Progress.”**  

---

## Step 3 – Investigation
- Read the alert description to gather context.  
- The alert was triggered when an employee attempted to connect to an external URL listed in the company’s blacklist/threat intelligence feeds.  
- The firewall successfully blocked the request, preventing the connection.  

### Actions Taken
- Scanned the blocked URL using *TryDetectThis* (in a real‑world setting I would use VirusTotal or AnyRun). The results confirmed the URL was malicious.  
- Checked the source IP against company records to identify the user. The activity was traced to **Hannah Harris (HR Department)**.  
- Queried ELK SIEM logs using the source IP to review activity around the time of the alert.  
  - Before the attempt: browsing business‑related topics (e.g., payroll systems).  
  - After the attempt: no further browsing activity observed.  
  - No evidence of malicious intent or compromise.  

![Lab 2 Screenshot](https://raw.githubusercontent.com/danyl-infosec/Alert-Triage-Lab-2/refs/heads/main/Lab%202%20Screenshot%205.png)

![Lab 2 Screenshot](https://raw.githubusercontent.com/danyl-infosec/Alert-Triage-Lab-2/refs/heads/main/Lab%202%20Screenshot%203.png)

---

## Step 4 – Analyst Actions
- Added analyst comment summarizing findings.  
- Updated verdict: **True Positive** (malicious URL confirmed).  
- Severity: **High** due to blacklist hit.  
- Impact: **Prevented** by firewall.  
- Escalation: **Not required**, as no impact or follow‑up activity was observed.  
- Closed the alert at Tier 1.  

---
