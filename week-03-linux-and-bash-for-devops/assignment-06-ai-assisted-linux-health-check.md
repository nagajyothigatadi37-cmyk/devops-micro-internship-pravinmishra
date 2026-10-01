# Assignment 6 — Build an AI-Assisted Linux Health Check (AI-Assisted Linux Incident Triage)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build a read-only Bash triage script that checks the health of your Ubuntu server and Nginx application, connect it to Claude Code as a reusable `/linux-triage` skill, simulate a controlled Nginx incident, use the skill to gather and analyze evidence, recover the service manually, and verify recovery. The workflow follows the Agentic Loop: Gather → Analyze → Human Act → Verify.

---

# Task 1 — Confirm the Healthy Baseline and Create the Workspace

## Goal

Confirm that Nginx and the React application are healthy before building the automation.

### Evidence

#### Screenshot 1 — Output of `systemctl is-active nginx`, `ss -ltn | grep ':80'`, and `curl -I http://localhost`

<img width="692" height="312" alt="Screenshot 2026-09-30 210440" src="https://github.com/user-attachments/assets/bab4ce17-bff4-4771-b0b2-e2e8aadfee3f" />


---

#### Screenshot 2 — Output of `pwd` and `find . -maxdepth 4 -type d | sort` showing the workspace folder structure

<img width="1123" height="245" alt="Screenshot 2026-09-30 210546" src="https://github.com/user-attachments/assets/08d8f5fc-a726-4b06-964b-be7e168ffac3" />


---

### Notes

Answer the following in your own words:

**1. What proves that Nginx is running?**

The command systemctl status nginx shows that Nginx is active (running). This confirms that the Nginx service is currently running.

---

**2. What proves that the server is listening for HTTP traffic?**

The command ss -tuln shows Nginx listening on port 80, which is the standard port for HTTP traffic. This proves the server is ready to accept HTTP connections.

---

**3. Why must you capture a healthy baseline before simulating an incident?**

A healthy baseline provides a reference for how the server behaves under normal conditions. After simulating an incident, you can compare the new results with the baseline to identify what changed and verify that the issue was successfully resolved.

---

# Task 2 — Create Project Context and Safety Rules in CLAUDE.md

## Goal

Tell Claude exactly what this project does and what it is not allowed to do.

### Evidence

#### Screenshot 3 — CLAUDE.md open in VS Code showing all four sections (Project Overview, Incident Workflow, Safety Rules, Output Rules)

<img width="1334" height="714" alt="Screenshot 2026-09-30 215250" src="https://github.com/user-attachments/assets/6a3d4786-b237-4487-b586-10d73b9e6e1f" />



---

### Notes

Answer the following in your own words:

**1. Why should Claude receive project-specific operational rules?**

Project-specific operational rules give Claude clear instructions about how the system should be managed. They help Claude follow the correct procedures, avoid unsafe actions, and provide responses consistent with the project's requirements.

---

**2. Why is the human required to execute the recovery command?**

The human must execute the recovery command to keep a person in control of potentially impactful system changes. Claude can suggest the appropriate command, but the human reviews and decides whether it is safe to run.

---

**3. Which rule prevents Claude from making an unsupported diagnosis?**

The rule that requires Claude to base diagnoses on verified evidence and avoid guessing when evidence is insufficient prevents unsupported diagnoses. This ensures Claude distinguishes between confirmed facts and assumptions.

---

# Task 3 — Use Agentic AI to Plan Before Writing the Script

## Goal

Use Claude Code to inspect the environment and produce a read-only plan before creating any Bash code.

### Evidence

#### Screenshot 4 — Claude Code showing the five-check plan and read-only inspection results

<img width="1357" height="618" alt="Screenshot 2026-09-30 213623" src="https://github.com/user-attachments/assets/ac9d9272-a641-446e-933c-876442b9adc2" />

<img width="1350" height="625" alt="Screenshot 2026-09-30 220419" src="https://github.com/user-attachments/assets/00342da1-ce1b-4264-a180-88aef1c2f54f" />



---

### Notes

Answer the following in your own words:

**1. Which part of this task represents the Gather phase?**

The Gather phase is the step where Claude inspects the existing project files, configuration, and system information to understand the current state before making any changes.

---

**2. Did Claude follow the instruction not to create files? How did you verify this?**

Yes. Claude followed the instruction and did not create any new files. I verified this by checking the project directory before and after the task and confirming that no additional files were created.

---

**3. Why is planning before coding useful in DevOps automation?**

Planning helps identify the required steps, dependencies, and possible risks before making changes. It reduces mistakes, prevents unnecessary modifications, and makes automation more predictable and reliable.

---

# Task 4 — Build the Linux Triage Bash Script

## Goal

Create one Bash script that gathers consistent Linux and Nginx health evidence.

### Evidence

#### Screenshot 5 — Top section of `linux-triage.sh` showing variables, thresholds, and the checks array

<img width="1338" height="343" alt="Screenshot 2026-09-30 221058" src="https://github.com/user-attachments/assets/863af148-8203-4315-ba3e-415449f50045" />


---

#### Screenshot 6 — Middle section showing check functions and conditionals

<img width="1344" height="574" alt="Screenshot 2026-09-30 221204" src="https://github.com/user-attachments/assets/3644fab3-f5b1-46f5-b97a-dadad0e6c1a2" />


---

#### Screenshot 7 — Bottom section showing the loop, summary function, and exit behavior

<img width="1338" height="609" alt="Screenshot 2026-09-30 221555" src="https://github.com/user-attachments/assets/64345095-295b-4a8b-b8d9-e9f2eb3f8d57" />


---

#### Screenshot 8 — Output of `bash -n scripts/linux-triage.sh` (no syntax errors) and `ls -l scripts/linux-triage.sh` showing executable permission

<img width="603" height="90" alt="Screenshot 2026-09-30 220937" src="https://github.com/user-attachments/assets/efcd5ecf-abba-4324-864f-178d77cdebe9" />


---

### Notes

Answer the following in your own words:

**1. What is stored in the checks array?**

The checks array stores the names of the health-check functions that the script needs to run, such as checking Nginx status, HTTP connectivity, and other server conditions.

---

**2. How does the `for` loop use that array?**

The for loop goes through each function name stored in the checks array and executes the corresponding health-check function one by one.

---

**3. Why are the health checks separated into functions?**

Separating the checks into functions makes the script easier to read, test, maintain, and troubleshoot. Each function performs one specific health check.

---

**4. What is the purpose of `$(...)` in this script?**

$(...) is command substitution in Bash. It runs the command inside the parentheses and replaces it with that command's output, allowing the output to be stored in a variable or used in another command.

---

**5. Why does the script use different exit codes for HEALTHY, WARN, and FAIL?**

Different exit codes allow other scripts or automation tools to understand the health-check result. They distinguish between a healthy system, a warning condition, and a failure that may require action.

---

# Task 5 — Run and Understand the Healthy-State Report

## Goal

Run the Bash script against the healthy server and verify that it creates a report.

### Evidence

#### Screenshot 9 — Output of `./scripts/linux-triage.sh` showing your Full Name and all five check results

<img width="1335" height="714" alt="Screenshot 2026-10-01 091020" src="https://github.com/user-attachments/assets/8bc476dd-5a59-4af8-aee6-1d06f6b21aed" />


---

#### Screenshot 10 — Output showing the captured exit code and final summary

<img width="1341" height="715" alt="Screenshot 2026-10-01 091153" src="https://github.com/user-attachments/assets/dd58482c-1e30-4e6e-b8d5-f4b8a1fbe637" />

<img width="763" height="197" alt="Screenshot 2026-10-01 091221" src="https://github.com/user-attachments/assets/09bd9716-3253-4f5f-a09a-29d43b05bf5c" />

---

### Notes

Answer the following in your own words:

**1. What is the overall status of your healthy baseline?**

The overall status of the healthy baseline is HEALTHY because Nginx is running, the server is listening for HTTP traffic, and the application is responding normally.

---

**2. Which exact Linux evidence proves the application is serving traffic?**

The curl -I http://localhost command returning HTTP/1.1 200 OK proves that the application is successfully serving HTTP traffic.

---

**3. Did your script return exit code 0 or 1? Explain why.**

The script returned exit code 0 because all the required health checks passed and the overall status was HEALTHY.

---

**4. What is the difference between a warning and a failure in this script?**

A warning indicates a condition that is not ideal but does not necessarily mean the application is down. A failure indicates a critical health check has failed and the application or service may not be functioning correctly.

---

# Task 6 — Create and Run the /linux-triage Skill

## Goal

Turn the Bash script into a reusable, manually invoked Agentic AI workflow.

### Evidence

#### Screenshot 11 — `SKILL.md` showing the frontmatter, allowed tool restrictions, and safety rules

Add your screenshot here.

---

#### Screenshot 12 — `/linux-triage` output for the healthy server

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. Why does this skill have Bash, Read, and Grep, but not Write?**

Add your answer here.

---

**2. Why is `disable-model-invocation: true` useful for this skill?**

Add your answer here.

---

**3. What part is performed by Bash, and what part is performed by Claude?**

Add your answer here.

---

**4. Why is this better than asking Claude "Is my server healthy?" without giving it evidence?**

Add your answer here.

---

# Task 7 — Simulate an Nginx Incident and Let the Skill Diagnose It

## Goal

Create a controlled service failure, gather evidence through Bash, and let Claude analyze the evidence without taking recovery action.

### Evidence

#### Screenshot 13 — Output showing Nginx is inactive and the HTTP request fails

Add your screenshot here.

---

#### Screenshot 14 — `/linux-triage` output showing failed evidence, most likely cause, and a suggested recovery command

Add your screenshot here.

---

#### Screenshot 15 — `incident-failure-report.txt` showing the failed checks and your Full Name

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. Which three checks failed?**

Add your answer here.

---

**2. What evidence supports the conclusion that Nginx is unavailable?**

Add your answer here.

---

**3. Did Claude execute the recovery command? Why is that important?**

Add your answer here.

---

**4. Which phase of the Agentic Loop is represented by the Bash report?**

Add your answer here.

---

**5. Which phase is represented by Claude's explanation?**

Add your answer here.

---

# Task 8 — Recover Manually, Verify Again, and Write the Incident Summary

## Goal

Recover the service as the human operator and prove that the system is healthy again.

### Evidence

#### Screenshot 16 — Output showing Nginx is active and `curl -I http://localhost` returns 200 OK

Add your screenshot here.

---

#### Screenshot 17 — Second `/linux-triage` output showing successful recovery with no FAIL results

Add your screenshot here.

---

#### Screenshot 18 — Output of `ls -lah reports` showing both `incident-failure-report.txt` and `recovery-report.txt`

Add your screenshot here.

---

#### Screenshot 19 — `incident-summary.md` showing all required sections and your Full Name

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What action did you execute manually?**

Add your answer here.

---

**2. What evidence proves that the service recovered?**

Add your answer here.

---

**3. Why is the second triage run necessary?**

Add your answer here.

---

**4. What could go wrong if an AI agent automatically restarted every failed service?**

Add your answer here.

---

**5. In one sentence, explain the difference between using AI as a chatbot and using AI in this agentic workflow.**

Add your answer here.

---

# Incident Summary

Fill in all seven sections below in your own words.

**Full Name:** Add your full name here

**Date:** DD/MM/YYYY

---

**1. Reported Symptom**

Add your answer here.

---

**2. Evidence Collected**

Add your answer here.

---

**3. Most Likely Cause**

Add your answer here.

---

**4. Human-Approved Recovery Action**

Add your answer here.

---

**5. Verification**

Add your answer here.

---

**6. Safety Decision**

Add your answer here.

---

**7. Agentic Loop Mapping**

Add your answer here.

---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

`Add your URL here`

---

#### Screenshot — Published LinkedIn post

Add your screenshot here.

---

# GitHub Repository URL

Paste the URL of your GitHub folder or repository containing the assignment files here:

`Add your URL here`

---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name must be visible in required screenshots and the Bash report
- All written answers must be in your own words
- Do not expose sensitive information (keys, passwords, AWS account IDs, tokens)
- GitHub URL must be included in this document

---

# Completion Checklist

- [ ] Task 1: Healthy baseline confirmed, workspace created (Screenshots 1–2, Notes answered)
- [ ] Task 2: CLAUDE.md created with all four sections (Screenshot 3, Notes answered)
- [ ] Task 3: Five-check plan produced by Claude using read-only tools (Screenshot 4, Notes answered)
- [ ] Task 4: `linux-triage.sh` created, syntax validated, executable permission set (Screenshots 5–8, Notes answered)
- [ ] Task 5: Healthy-state report generated with no FAIL result (Screenshots 9–10, Notes answered)
- [ ] Task 6: `/linux-triage` skill created and run successfully on healthy server (Screenshots 11–12, Notes answered)
- [ ] Task 7: Nginx incident simulated, failed evidence captured, Claude did not execute recovery (Screenshots 13–15, Notes answered)
- [ ] Task 8: Nginx recovered manually, recovery verified, reports saved, incident summary complete (Screenshots 16–19, Notes answered)
- [ ] Incident summary contains all seven required sections
- [ ] LinkedIn post published and URL submitted
- [ ] Full Name visible in all required screenshots and the Bash report
- [ ] Skill does not have Write permission
- [ ] Skill did not execute any recovery commands
- [ ] No sensitive data exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
