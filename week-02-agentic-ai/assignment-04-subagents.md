# Assignment 4 — Building Your AI Team

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build and configure a set of specialized AI subagents inside your project. You will learn how different models and tool permissions define agent behavior, and you will trigger two real agent delegations to analyze security and cost aspects of your Terraform infrastructure.

---

# Task 1 — Create the Agents Folder and Add Files

## Goal

Create the `.claude/agents/` directory and add all required agent files.

### Evidence

#### Screenshot 1 — VS Code sidebar showing `.claude/agents/` with all 3 files

<img width="1051" height="712" alt="Screenshot 2026-09-20 184841" src="https://github.com/user-attachments/assets/864c08e0-3208-4314-89e1-f3d3a3bcac43" />


---

# Task 2 — Compare the Agent Configurations

## Goal

Analyze the configuration differences between the three agents and demonstrate understanding of model and tool selection.

### Written Answers

#### 1. Why does the cost optimizer use Haiku instead of Sonnet?

 Haiku is generally chosen for cost-sensitive tasks because it is faster and less expensive while still being suitable for simpler optimization work.

---

#### 2. Why does the security auditor NOT have Write in its tools list?

A security auditor should inspect/analyze the code without modifying files. Removing Write helps keep the audit read-only and prevents accidental changes.

---

#### 3. Why does the tf-writer use `inherit` instead of a specific model?

inherit means the agent uses the model/configuration inherited from its parent or calling context, rather than forcing a particular model. This makes the agent more flexible and consistent with the environment in which it is invoked.


---

### Evidence

#### Screenshot 2 — `security-auditor.md` frontmatter showing model and tools configuration

<img width="1061" height="726" alt="Screenshot 2026-09-20 190444" src="https://github.com/user-attachments/assets/a24b2209-ed26-446d-9bd9-07e8a7c022a4" />


---

#### Screenshot 3 — `cost-optimizer.md` frontmatter showing the model and tools configuration

<img width="1054" height="716" alt="Screenshot 2026-09-20 190633" src="https://github.com/user-attachments/assets/4d70d5fb-b593-41ce-9f6e-b0987f531c68" />


---

# Task 3 — Run the Security Auditor

## Goal

Trigger the security auditor agent and analyze the generated security report for your Terraform infrastructure.

### Evidence

#### Screenshot 4 — The delegation message showing Claude launched the security-auditor

<img width="461" height="603" alt="Screenshot 2026-09-20 205525" src="https://github.com/user-attachments/assets/333ee86d-bd8d-4e6d-ab4b-de23a882d67c" />


---

#### Screenshot 5 — Security audit report output

<img width="306" height="424" alt="Capture20260920210008" src="https://github.com/user-attachments/assets/a81b39c0-d54a-4636-a24c-d97055df960f" />


---

# Task 4 — Run the Cost Optimizer

## Goal

Trigger the cost optimizer agent and review the generated cost optimization report.

### Evidence

#### Screenshot 6 — The full cost optimization report
<img width="788" height="576" alt="Screenshot 2026-09-20 211831" src="https://github.com/user-attachments/assets/662701eb-e7b3-4bf4-953f-b379df25d237" />


---

# Submission Instructions

- Ensure all agent files are committed in `.claude/agents/`
- Complete all written answers in your GitHub Repo
- Push final changes to your forked GitHub repository

---

## GitHub Repository URL

Paste your forked repository URL here:

`Add your URL here`

---

# Completion Checklist

- [ ] `.claude/agents/` folder contains all 3 agent files
- [ ] Screenshot 2 shows correct `security-auditor.md` configuration
- [ ] Screenshot 3 shows correct `cost-optimizer.md` configuration
- [ ] All 3 written answers completed 
- [ ] Security auditor executed successfully
- [ ] Cost optimizer executed successfully
- [ ] Security report is visible with findings
- [ ] Cost report is visible with recommendations
- [ ] All required screenshots added
- [ ] GitHub repo updated with agents

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
