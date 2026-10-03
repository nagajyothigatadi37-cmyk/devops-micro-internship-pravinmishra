# Assignment 3 — CodeTrack: Branching Workflow (Add & Verify a Contact Page)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will add a new Contact page to CodeTrack using a clean feature-branch workflow. You will keep each change in a separate commit, prove that your default branch remains unchanged before the merge, and validate the result after merging.

---

# Task 1 — Confirm Repository State and Default Branch

## Goal

Start from a clean default branch (`main` or `master`) and confirm the repository status.

### Evidence

#### Screenshot 1 — Output of `git status` and `git branch` showing a clean status and the default branch checked out

<img width="1108" height="633" alt="Screenshot 2026-10-02 204400" src="https://github.com/user-attachments/assets/6f9da992-bb37-465a-9aeb-3ccf7972eecb" />

---

# Task 2 — Create and Switch to a Feature Branch

## Goal

Create a branch named exactly `feature/contact-page` and switch to it.

### Evidence

#### Screenshot 2 — Output of `git checkout -b feature/contact-page` and `git branch` showing `* feature/contact-page`

<img width="873" height="254" alt="Screenshot 2026-10-02 204734" src="https://github.com/user-attachments/assets/db12234c-e2f4-4e3f-8dea-de06376e7cf7" />


---

# Task 3 — Add contact.html on the Feature Branch

## Goal

Create `contact.html` with the provided content and commit it alone using the message `feat(contact): add Contact page`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `contact.html`

<img width="870" height="85" alt="Screenshot 2026-10-02 205633" src="https://github.com/user-attachments/assets/d87c400d-88aa-40b2-866a-a72d93ef6c16" />


---

#### Screenshot 4 — Output of `git commit`

<img width="790" height="113" alt="Screenshot 2026-10-02 205707" src="https://github.com/user-attachments/assets/076c4136-e677-4491-965e-9e7ef5daded2" />


---

#### Screenshot 5 — Output of `git log --oneline -3` showing the new commit

<img width="811" height="112" alt="Screenshot 2026-10-02 205726" src="https://github.com/user-attachments/assets/dc5e8728-6c9c-4b86-8f2e-9710a79ec267" />


---

# Task 4 — Add the Contact Link to index.html

## Goal

Add the provided Contact Page link to `index.html` and commit it separately using the message `feat(nav): add Contact Page link`.

### Evidence

#### Screenshot 6 — Output of `git status` showing `index.html` as modified before staging

<img width="816" height="378" alt="Screenshot 2026-10-02 210408" src="https://github.com/user-attachments/assets/1dc14ef5-3de2-46e7-a6b8-b8b107cfe5e7" />


---

#### Screenshot 7 — Output of `git commit`

<img width="872" height="218" alt="Screenshot 2026-10-02 210429" src="https://github.com/user-attachments/assets/e31548c9-141f-4601-a482-328e21d0851e" />


---

#### Screenshot 8 — Browser showing the Contact Page link on the homepage while on `feature/contact-page`

<img width="716" height="460" alt="Screenshot 2026-10-03 120335" src="https://github.com/user-attachments/assets/5918fa7d-0926-46d0-bd1b-57ea8a6e72ba" />


---

# Task 5 — Verify Isolation (Prove the Default Branch Is Unchanged)

## Goal

Switch back to the default branch and confirm that `contact.html` and the Contact Page link do not exist there yet.

### Evidence

#### Screenshot 9 — Terminal showing the checkout and `ls` output, proving `contact.html` is absent

Add your screenshot here.

---

#### Screenshot 10 — Browser showing the homepage on the default branch with no Contact Page link

Add your screenshot here.

---

# Task 6 — Merge the Feature Branch into the Default Branch

## Goal

Merge `feature/contact-page` into your default branch and confirm the Contact page works.

### Evidence

#### Screenshot 11 — Output of `git merge feature/contact-page`

Add your screenshot here.

---

#### Screenshot 12 — Output of `ls` showing `contact.html` after the merge

Add your screenshot here.

---

#### Screenshot 13 — Browser showing the Contact page opened from the homepage link on the default branch

Add your screenshot here.

---

# Task 7 — Inspect History (Graph View)

## Goal

Display the repository history as a graph and locate both feature commits.

### Evidence

#### Screenshot 14 — Full output of `git log --oneline --graph --decorate --all`

Add your screenshot here.

---

# Task 8 — Optional Cleanup (Delete the Feature Branch)

## Goal

Delete the merged `feature/contact-page` branch to keep your branch list clean.

### Evidence

#### Screenshot 15 (Optional) — Output showing `feature/contact-page` deleted and no longer listed

Add your screenshot here.

---

# Submission Instructions

- Tasks 1–7 are required; Task 8 is optional
- Add all required screenshots in your submission
- Evidence must show `contact.html` and the homepage link were absent before merging, and working after merging
- Do not expose passwords, access tokens, or private keys

---

# Completion Checklist

- [ ] Repository confirmed clean on the default branch (Screenshot 1)
- [ ] `feature/contact-page` created and checked out (Screenshot 2)
- [ ] `contact.html` added in its own commit (Screenshots 3–5)
- [ ] Homepage Contact link added in a separate commit (Screenshots 6–8)
- [ ] Default branch proven unchanged before merge (Screenshots 9–10)
- [ ] Feature branch merged and Contact page verified (Screenshots 11–13)
- [ ] Graph history reviewed (Screenshot 14)
- [ ] Optional cleanup completed (Screenshot 15)
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
