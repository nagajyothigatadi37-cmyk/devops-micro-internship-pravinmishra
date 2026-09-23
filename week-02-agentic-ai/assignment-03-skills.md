# Assignment 3 — Building Your Command Center

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build a local Claude Skills system by creating the `.claude/skills/` folder structure, adding predefined skill files, and executing a real agentic command (`/scaffold-terraform`) to generate infrastructure code. You will also observe how skills enforce tool restrictions and enable controlled automation.

---

# Task 1 — Create the Skill Folder Structure

## Goal

Create the required `.claude/skills/` directory structure for all skills.

### Evidence

#### Screenshot 1 — VS Code sidebar showing `.claude/skills/` folder with all 4 subfolders visible

<img width="1012" height="710" alt="Screenshot 2026-09-20 144129" src="https://github.com/user-attachments/assets/5e0def2a-f325-4e4b-9608-adcae3506172" />


---

# Task 2 — Add the Skill Files

## Goal

Place all required skill files into their correct directories and verify their configuration.

### Evidence

#### Screenshot 2 — `.claude/skills/scaffold-terraform/` open in VS Code showing both `SKILL.md` and `template-spec.md`

<img width="1014" height="714" alt="Screenshot 2026-09-20 144855" src="https://github.com/user-attachments/assets/d78582bd-b1ce-4305-898e-a9b08490cd18" />


---

#### Screenshot 3 — Screenshot 3 — `tf-plan/SKILL.md` frontmatter showing `allowed-tools: Bash, Read, Grep` (no Write) and `disable-model-invocation: true`

<img width="1018" height="714" alt="Screenshot 2026-09-20 145525" src="https://github.com/user-attachments/assets/974fb32f-49aa-4c8e-bd0c-6adb3dd7d9ca" />


---

# Task 3 — Run /scaffold-terraform

## Goal

Execute the `/scaffold-terraform` skill to generate a full Terraform infrastructure setup.

### Evidence

#### Screenshot 4 — Claude's response showing the scaffold complete with the file list

<img width="1536" height="551" alt="WhatsApp Image 2026-09-20 at 3 33 10 PM (1)" src="https://github.com/user-attachments/assets/f2e21f74-c137-4e27-a072-11d8328783a9" />


---

#### Screenshot 5 — VS Code sidebar showing the `terraform/` folder with all generated files inside

<img width="1038" height="674" alt="Screenshot 2026-09-20 154147" src="https://github.com/user-attachments/assets/db95e47b-8fc9-4c0a-8884-724cea71ee74" />


---

# Task 4 — Run terraform init and /tf-plan

## Goal

Initialize Terraform and execute the `/tf-plan` skill to observe plan execution and output analysis.

### Evidence

#### Screenshot 6 — Claude's `/tf-plan` response showing it ran the command and analyzed the result (pass or auth error both count)

<img width="1037" height="713" alt="Screenshot 2026-09-20 160100" src="https://github.com/user-attachments/assets/7789a56f-0861-4d2e-b96b-ae7101170851" />


---

# Submission Instructions

- Ensure `.claude/skills/` folder and all skill files are committed to your GitHub repository
- Run all commands successfully and capture required screenshots
- Push final changes to your forked repository

---

## GitHub Repository URL

Paste your forked repository URL here:

https://github.com/nagajyothigatadi37-cmyk/Ultimate-Agentic-DevOps-with-Claude-Code.git
https://github.com/nagajyothigatadi37-cmyk/devops-micro-internship-pravinmishra

## LinkedIn post URL

Paste your forked repository URL here:

https://lnkd.in/p/dSFdWtw9
---

# Completion Checklist

- [✅] `.claude/skills/` folder created with all 4 skill folders
- [✅] All skill files placed correctly
- [✅] `tf-plan/SKILL.md` shows correct `allowed-tools` restrictions
- [✅] `/scaffold-terraform` executed successfully
- [✅] Terraform files generated inside `terraform/` folder
- [✅] `terraform init` executed successfully
- [✅] `/tf-plan` executed and output analyzed by Claude
- [✅] All required screenshots added
- [✅] GitHub repository URL included
- [✅] LinkedIn post URL included

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
