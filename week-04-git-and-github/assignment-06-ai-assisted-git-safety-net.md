# Assignment 6 — Building an AI-Assisted Git Safety Net (PR Ready Check)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In Week 2 you built Claude Code hooks that block a dangerous action *before* it happens (`PreToolUse`), and a restricted skill that could look but not touch (`allowed-tools` without `Write`). In this assignment you will discover that Git has the exact same idea, decades older: a **pre-commit hook** that blocks a commit before it's created.

You will build both halves of a real "PR Ready" workflow:

1. A **Git hook that follows fixed rules** — scans staged changes for hardcoded secrets and oversized files and refuses the commit. No AI involved, no guessing, just a rule that gives the same answer every time.
2. A **restricted Claude Code skill** (`/pr-ready`) that reads your staged diff and drafts a Pull Request title, description, and a short list of things worth a second look — the kind of judgment a fixed rule can't make (mixed changes, missing context, unclear intent). The skill never commits, pushes, or opens the PR. You do that yourself, using its draft as a starting point.

This mirrors the Agentic Loop from Week 3's Linux triage assignment: **Gather → Analyze → Human Act → Verify**. The hook and the skill both gather and analyze; only you act.

---

# Task 0 — Confirm Your Fork and Create a Feature Branch

## Goal

Confirm you are working in your own fork, then create a dedicated branch for this assignment.

### Evidence

#### Screenshot 1 — Output of git remote -v and git branch showing the new branch

<img width="1150" height="336" alt="Screenshot 2026-10-04 195129" src="https://github.com/user-attachments/assets/390baf16-a557-4cf5-8bfd-8ff042f1733c" />


---

### Notes

**1. Why create a dedicated branch instead of doing this work on main?**

A dedicated branch keeps `main` stable while you work on a specific change.
It also makes the change easier to review, test, and merge through a Pull Request.


---

# Task 1 — Stage a Change With Realistic Risk

## Goal

On your own fork of this repository (the one you've been submitting your DMI work in since onboarding), create a new branch and stage a change that a real reviewer should catch: a hardcoded-looking secret and a leftover debug statement.

### Evidence

#### Screenshot 1 — Output of  `git status` showing the staged file on feature/ai-pr-ready

<img width="1094" height="333" alt="Screenshot 2026-10-04 195937" src="https://github.com/user-attachments/assets/90ce403e-aff7-4a12-9d0d-268848701ddb" />


---

### Notes

**1. Why does this assignment use an obviously fake key instead of a real one?**

It uses an obviously fake key so students can practice the workflow **without exposing a real secret or credential**.
This teaches safe handling of sensitive information while avoiding security risks.


---

# Task 2 — Write a Real Git Pre-Commit Hook

## Goal

Create a tracked, shareable pre-commit hook that blocks a commit containing secret-like patterns or files over 1MB.

### Evidence

#### Screenshot 2 — `hooks/pre-commit` open in VS Code showing the full script

<img width="1335" height="709" alt="Screenshot 2026-10-04 201234" src="https://github.com/user-attachments/assets/f2570633-7c3f-4d90-91a8-1e28f20794e2" />


---

#### Screenshot 3 — Output of `git config core.hooksPath` confirming it points to `hooks`

<img width="1070" height="136" alt="Screenshot 2026-10-04 201349" src="https://github.com/user-attachments/assets/b19e2f16-db07-46e4-8589-94ad22b1db9c" />


---

### Notes

**1. Why is `hooks/pre-commit` tracked in the repo instead of living only in `.git/hooks/`?**

It is tracked so the pre-commit hook can be shared with everyone who clones the repository. The .git/hooks/ directory is local to each Git clone and is not normally committed.

---

**2. Compare this to `PreToolUse` from Week 2 Assignment 6. What does each one intercept, and what do they have in common?**

pre-commit intercepts a Git commit before it is created, while PreToolUse intercepts a tool execution before Claude runs it. Both act as pre-execution checkpoints that can validate or block an action.

---

# Task 3 — Prove the Hook Blocks the Risky Commit

## Goal

Attempt to commit the staged file from Task 1 and show the hook rejecting it.

### Evidence

#### Screenshot 4 — Terminal showing `git commit` rejected with the hook's "BLOCKED" message naming the exact file

<img width="1097" height="107" alt="Screenshot 2026-10-04 211629" src="https://github.com/user-attachments/assets/ae892631-c61d-4fb6-87f6-c36a7f37f52f" />


---

### Notes

**1. Which line in `hooks/pre-commit` matched your fake key, and why did it match?**

The line that checks for the AKIA pattern matched the fake key because the key started with AKIA. The hook uses this fixed pattern to detect strings that look like AWS access keys.

---

**2. Could this hook have caught a poorly-named variable that stores a secret without the `AKIA` prefix? What does that tell you about the limits of a fixed rule like this?**

No. If the secret did not contain the AKIA pattern, the hook would not detect it. This shows that fixed rules can only catch known patterns and may miss secrets that use different formats or naming conventions.

---

# Task 4 — Build the `/pr-ready` Skill

## Goal

Create a manually invoked Claude Code skill that reads your staged changes and produces a PR-readiness report and a draft PR description — without writing, committing, or pushing anything itself.

### Evidence

#### Screenshot 5 — `SKILL.md` frontmatter showing `allowed-tools: Bash, Read, Grep` (no `Write`) and `disable-model-invocation: true`

<img width="1338" height="509" alt="Screenshot 2026-10-04 213658" src="https://github.com/user-attachments/assets/baecfbf2-22c2-4ee5-a806-9be0b4744a3f" />


---

#### Screenshot 6 — `/pr-ready` output while the risky file is still staged, showing it flagged the secret and/or debug statement

<img width="892" height="484" alt="Screenshot 2026-10-04 214318" src="https://github.com/user-attachments/assets/c2236e2d-aa4c-45fb-8f04-8e95598e4cc2" />

<img width="1041" height="519" alt="Screenshot 2026-10-04 214410" src="https://github.com/user-attachments/assets/fe14c967-dbde-4a52-a9a0-d889d97e8d0c" />


---

### Notes

**1. Why does `/pr-ready` have `Bash` and `Read` but not `Write`?**

Bash and Read allow /pr-ready to inspect the repository and run checks. It does not have Write because it should not modify files automatically, keeping the review process safer.

---

**2. The pre-commit hook and `/pr-ready` both looked at the same staged diff. Did they flag the same things? What did one catch that the other didn't?**

No. The pre-commit hook caught the fake AKIA-style key, while /pr-ready could perform broader review checks on the staged changes. This shows that automated checks can catch different types of problems depending on their rules and purpose.

---

# Task 5 — Fix the Issues and Re-Verify

## Goal

Remove the secret and debug statement, then prove both gates now pass clean.

### Evidence

#### Screenshot 7 — `git commit` succeeding after the fix (no BLOCKED message)

<img width="1082" height="231" alt="Screenshot 2026-10-04 214613" src="https://github.com/user-attachments/assets/e5a4acf0-5915-4b48-bfe9-e09f75452097" />


---

#### Screenshot 8 — Second `/pr-ready` run showing a clean risk report and a drafted PR title + description

<img width="1058" height="531" alt="Screenshot 2026-10-04 214712" src="https://github.com/user-attachments/assets/09cc814f-1223-41c6-ab48-4b4e6020fbba" />

<img width="955" height="532" alt="Screenshot 2026-10-04 214731" src="https://github.com/user-attachments/assets/2a031488-f043-4665-8cf8-4925b9cafabc" />

<img width="976" height="349" alt="Screenshot 2026-10-04 214748" src="https://github.com/user-attachments/assets/8e7e50d1-5e25-4135-958f-12d76b441a09" />


---

### Notes

**1. What exactly did you change to satisfy the pre-commit hook?**

I removed the **fake `AKIA`-style secret/key from the staged changes** so that the `pre-commit` hook no longer detected it. The rest of the intended changes were kept unchanged.


---

# Task 6 — Push and Open a Pull Request Using the AI Draft

## Goal

Push your branch and open a real Pull Request, using `/pr-ready`'s drafted title and description as your starting point — read it critically and edit before you use it.

**Important:** Open this Pull Request with base repository set to **your own fork** — not the shared upstream `pravinmishraaws/devops-micro-internship-pravinmishra` repository. This assignment's hook and skill files are your own practice work, not a change meant for the shared class repo.

### Evidence

#### Screenshot 9 — Your Pull Request showing the base repository is your own fork, plus the title and description, with the `/pr-ready` draft visible for comparison (paste it in the PR conversation or your notes below)

<img width="1347" height="677" alt="Screenshot 2026-10-04 215051" src="https://github.com/user-attachments/assets/f2c2e384-0503-4cf9-a511-ad70cd429e92" />


---

#### PR Link

https://github.com/nagajyothigatadi37-cmyk/devops-micro-internship-interviews/pull/1

---

### Notes

**1. What, if anything, did you edit in the AI's drafted PR description before using it? Why?**

I reviewed the AI-generated PR description and made any necessary edits to ensure the details, branch names, and changes accurately matched my work. This helped keep the PR description clear and truthful.

---

**2. If you had blindly copy-pasted the AI's draft without reading it, what could go wrong?**

It could contain incorrect claims, wrong file names, branch names, or changes I did not actually make, which could mislead the reviewer.

---

**3. Why does this PR need to target your own fork instead of the shared upstream repository?**

The fork is my own copy where I have permission to push changes. The shared upstream repository is maintained by the project owners, so my changes should be submitted there through a PR rather than pushing directly.

---

# Task 7 — Map the Workflow to the Agentic Loop

## Goal

Explain this assignment's workflow using the same Gather → Analyze → Human Act → Verify structure from Week 3.

### Notes

**1. Which step(s) represent Gather?**

The steps where Claude reads the repository files, checks the staged diff, and collects the relevant Git information represent Gather.

---

**2. Which step(s) represent Analyze?**

The steps where Claude reviews the collected information, checks for issues such as secrets, and prepares the PR description represent Analyze.

---

**3. Which step is Human Act, and why must a human — not Claude — run `git commit`, `git push`, and open the PR?**

The final commit, push, and PR creation represent Human Act. A human must perform them because these actions change repository history and publish changes, so they require human review, approval, and accountability.

---

**4. Which step is Verify?**

The final check after the human action, where the repository, commit, push, and PR are reviewed to confirm everything was completed correctly, represents Verify.

---

**5. In one or two sentences: why do you need *both* the fixed-rule pre-commit hook and the AI skill? Isn't one enough?**

The pre-commit hook provides fast, consistent protection against known patterns, while the AI skill can perform broader contextual analysis. Together, they provide stronger coverage than either one alone.

---

# Task 8 — LinkedIn Post

## Goal

Publish a LinkedIn post summarizing what you built and what you learned about combining fixed-rule safety checks with AI-assisted review.

### Evidence

#### LinkedIn Post URL

https://lnkd.in/p/d6iCubSk

---

## Key Learnings

Add 3-5 bullet points on what you learned this week.

* Learned how Git pre-commit hooks can automatically detect risky patterns such as fake secrets before a commit.
* Learned how Claude Code skills can review staged changes without modifying, committing, or pushing files.
* Learned the importance of using fixed-rule checks together with AI-based analysis for better coverage.
* Learned the Gather → Analyze → Human Act → Verify workflow for safer AI-assisted development.
* Learned that AI-generated PR descriptions should always be reviewed and verified by a human before publishing.

---

# Submission Instructions

- Ensure `hooks/pre-commit` and `.claude/skills/pr-ready/SKILL.md` are committed to your GitHub repository
- Add all required screenshots to your submission
- All written answers must be in your own words
- Do not use a real secret or credential anywhere in your submission — the fake key in Task 1 is intentional and must stay clearly fake
- Open your Pull Request against your own fork, not the shared upstream repository
- Push your final changes to your forked repository
- Include your PR link and LinkedIn post URL

---

## GitHub Repository URL

Paste your forked repository URL here:

https://github.com/nagajyothigatadi37-cmyk/devops-micro-internship-interviews

---

# Completion Checklist

- [✅] Branch `feature/ai-pr-ready` created with a staged file containing a fake secret and a debug statement
- [✅] `hooks/pre-commit` created and tracked in the repo (not only in `.git/hooks/`)
- [✅] `core.hooksPath` configured to point at `hooks/`
- [✅] Pre-commit hook shown blocking the risky commit
- [✅] `.claude/skills/pr-ready/SKILL.md` created with correct `allowed-tools` (no `Write`) and `disable-model-invocation: true`
- [✅] `/pr-ready` run against the risky diff and shown flagging issues
- [✅] Risky file fixed; `git commit` succeeds cleanly
- [✅] `/pr-ready` re-run showing a clean report and drafted PR title/description
- [✅] Pull Request opened using the AI draft as a starting point, with your own fork as the base repository (not upstream), PR link included
- [✅] Agentic Loop mapping (Task 7) completed in your own words
- [✅] LinkedIn post published and URL submitted
- [✅] All required screenshots added
- [✅] GitHub repository URL provided

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
