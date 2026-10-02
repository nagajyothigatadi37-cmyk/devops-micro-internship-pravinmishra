# Assignment 2 — CodeTrack: Tracking, Staging, Committing + Deploy to EC2

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will track and stage project files, create two meaningful Git commits in `CodeTrack`, verify your commit history, and deploy the CodeTrack static website to an EC2 instance using Nginx. This connects local version-control practice with a basic manual deployment workflow used in real DevOps environments.

---

# Task 1 — Verify Git Setup and Enter the Repository

## Goal

Confirm that Git works and that you are inside the correct `CodeTrack` repository.

### Evidence

#### Screenshot 1 — Output of `pwd` showing you're inside `CodeTrack`

<img width="482" height="213" alt="Screenshot 2026-10-02 124450" src="https://github.com/user-attachments/assets/479b5176-a97e-4631-a10f-b47b710dc7d9" />


---

#### Screenshot 2 — Output of `git status` showing no "not a git repository" error

<img width="552" height="154" alt="Screenshot 2026-10-02 124505" src="https://github.com/user-attachments/assets/227992b1-49d0-4644-a965-68b2352e5575" />


---

# Task 2 — Create index.html and style.css

## Goal

Create the two starter UI files inside `CodeTrack`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `index.html` and `style.css`

<img width="505" height="144" alt="Screenshot 2026-10-02 124717" src="https://github.com/user-attachments/assets/b8fb7b81-f4d3-4eba-975a-bd3939da4cc8" />


---

# Task 3 — Add Starter Content

## Goal

Copy the provided starter HTML and CSS content into your local `index.html` and `style.css` files.

### Evidence

#### Screenshot 4 — Your editor showing the contents of `index.html` and `style.css`

<img width="1041" height="713" alt="Screenshot 2026-10-02 142836" src="https://github.com/user-attachments/assets/80155638-06c4-4ee7-8245-aaa65cffdd21" />

<img width="992" height="707" alt="Screenshot 2026-10-02 142807" src="https://github.com/user-attachments/assets/b1e39880-1875-40eb-9edc-ac583b1f59ed" />

---

# Task 4 — Track and Stage Files Correctly

## Goal

Confirm both files show as untracked, then stage them individually with `git add`.

### Evidence

#### Screenshot 5 — Output of `git status` showing both files as untracked

<img width="1032" height="552" alt="Screenshot 2026-10-02 143809" src="https://github.com/user-attachments/assets/b98d25ca-f9e1-4582-b2e1-6610cafdbeb4" />


---

#### Screenshot 6 — Output of `git status` showing both files staged under "Changes to be committed"

<img width="1031" height="671" alt="Screenshot 2026-10-02 143910" src="https://github.com/user-attachments/assets/c92999d4-00a2-49f5-b821-46e1008f1ce4" />


---

# Task 5 — Create the First Commit (Clean Initial Commit)

## Goal

Commit the staged starter files using the message `Initial UI scaffold: add index.html and style.css`, then check the log.

### Evidence

#### Screenshot 7 — Output of `git commit`

<img width="804" height="207" alt="Screenshot 2026-10-02 144158" src="https://github.com/user-attachments/assets/f81313c3-9840-46a4-96f6-b7d285758c61" />


---

#### Screenshot 8 — Output of `git log --oneline` showing the first commit

<img width="813" height="675" alt="Screenshot 2026-10-02 144222" src="https://github.com/user-attachments/assets/d3e09371-59ef-46a8-9c6b-908df29b9763" />


---

# Task 6 — Modify index.html and Create a Second Commit

## Goal

Follow the instruction comment inside `index.html` to update the Student Name and Group Name, then commit that change separately using the message `Update homepage content: heading, tagline, CTA button`.

### Evidence

#### Screenshot 9 — Browser showing the updated page with your Student Name and Group Name visible

<img width="701" height="465" alt="Screenshot 2026-10-02 151546" src="https://github.com/user-attachments/assets/875ef08e-cf60-48c4-bc7e-afc31d7276b3" />


<img width="805" height="628" alt="Screenshot 2026-10-02 150555" src="https://github.com/user-attachments/assets/97378d99-1dcc-48b4-bf31-308ed494f7c3" />

---

#### Screenshot 10 — Output of `git status` showing `index.html` as modified

<img width="1044" height="537" alt="Screenshot 2026-10-02 144854" src="https://github.com/user-attachments/assets/745556e3-ceca-4fe9-b3f4-486d24465f2a" />


---

#### Screenshot 11 — Output of `git commit`

<img width="821" height="532" alt="Screenshot 2026-10-02 144917" src="https://github.com/user-attachments/assets/194691cf-619e-45ec-9aa8-fd185458342b" />


---

#### Screenshot 12 — Output of `git log --oneline` showing two commits

<img width="791" height="681" alt="Screenshot 2026-10-02 144956" src="https://github.com/user-attachments/assets/b3d7c79c-3d2a-4e90-9e04-7bd836f07cce" />


---

# Task 7 — Deploy to EC2 with Nginx (Static Website)

## Goal

Install and start Nginx on your EC2 instance, then copy `index.html` and `style.css` into the Nginx web root.

### Evidence

#### Screenshot 13 — Output of `systemctl status nginx --no-pager` showing Nginx `active (running)`

Add your screenshot here.

---

#### Screenshot 14 — Output of `curl -I http://localhost` showing `HTTP/1.1 200 OK`

Add your screenshot here.

---

#### Screenshot 15 — Browser showing the CodeTrack site loaded at `http://<EC2_PUBLIC_IP>`, with your Full Name and Group Name visible

<img width="705" height="458" alt="Screenshot 2026-10-02 152105" src="https://github.com/user-attachments/assets/bc45dbc7-f76f-4942-8599-63529db07964" />


---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

`Add your URL here`

---

#### Screenshot — LinkedIn post showing the deployed CodeTrack application

Add your screenshot here.

---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name and Group Name must be visible in the deployed application evidence
- `git log --oneline` output must show at least two meaningful commits
- Do not expose AWS access keys, passwords, private key contents, or other sensitive information

---

# Completion Checklist

- [ ] `CodeTrack` repository verified with `git status` (Screenshots 1–2)
- [ ] `index.html` and `style.css` created and populated (Screenshots 3–4)
- [ ] Starter files staged and committed in the first commit (Screenshots 5–8)
- [ ] Student Name and Group Name updated in `index.html` (Screenshot 9)
- [ ] Second controlled commit created (Screenshots 10–12)
- [ ] Nginx active on the EC2 instance and CodeTrack reachable via its public IP (Screenshots 13–15)
- [ ] LinkedIn post published and URL submitted
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
