# Assignment 2 — Deploy Personal Portfolio Website on S3

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will deploy a static personal portfolio website quickly and reliably using Amazon S3 Static Website Hosting. You will download the portfolio template, create an S3 bucket, upload the static files, enable static website hosting, configure public read access, and validate the deployment through the S3 website endpoint.

---

# Task 1 — Download the Website Template Locally

## Goal

Download or clone the portfolio website template from GitHub and confirm `index.html` is present.

### Evidence

#### Screenshot 1 — File Explorer or terminal showing the template folder contents with `index.html` visible

<img width="1342" height="713" alt="Screenshot 2026-10-25 153351" src="https://github.com/user-attachments/assets/074268e3-0e7d-4f72-8b40-5257e242f298" />


---

# Task 2 — Create an S3 Bucket for Website Hosting

## Goal

Create a globally unique S3 bucket in your chosen AWS region.

### Evidence

#### Screenshot 2 — S3 bucket created screen showing the bucket name and region

<img width="1356" height="577" alt="Screenshot 2026-10-25 154813" src="https://github.com/user-attachments/assets/ad83641c-4bad-449a-870c-995a5c0d725d" />


---

# Task 3 — Upload Website Files to the Bucket

## Goal

Upload the contents of the template folder (not the folder itself) so `index.html` sits at the bucket root.

### Evidence

#### Screenshot 3 — S3 bucket Objects view showing `index.html` at the top or root level

<img width="1365" height="624" alt="Screenshot 2026-10-25 155855" src="https://github.com/user-attachments/assets/c4481758-d091-4b32-9cff-a61ddd6a7141" />


---

# Task 4 — Enable Static Website Hosting

## Goal

Enable S3 Static Website Hosting with `index.html` as the index document and `error.html` as the error document.

### Evidence

#### Screenshot 4 — Static website hosting enabled screen showing the Website endpoint

<img width="1357" height="624" alt="Screenshot 2026-10-25 172146" src="https://github.com/user-attachments/assets/8fce5045-6e9e-461c-b82d-93c9eef0b7b3" />


---

# Task 5 — Make the Website Public (Bucket Policy + Permissions)

## Goal

Adjust Block Public Access settings and save a bucket policy that grants public read access to the website objects.

### Evidence

#### Screenshot 5 — Bucket policy page showing the policy saved successfully, with the bucket name visible

<img width="1358" height="391" alt="Screenshot 2026-10-25 173849" src="https://github.com/user-attachments/assets/debc0c73-9829-4cb3-99bd-98d80781a44b" />

<img width="1354" height="591" alt="Screenshot 2026-10-25 173932" src="https://github.com/user-attachments/assets/bce2fe15-67da-482b-b39c-50f09e8af849" />

---

# Task 6 — Verify Website Works (Public Endpoint Test)

## Goal

Load the site through the S3 website endpoint and confirm the homepage, images, and CSS load correctly.

### Evidence

#### Screenshot 6 — Browser showing the live website with the S3 website endpoint visible in the address bar

<img width="1350" height="624" alt="Screenshot 2026-10-25 175355" src="https://github.com/user-attachments/assets/7958d09e-d974-46ba-bd92-4e1ef7b0dc6c" />


<img width="1341" height="673" alt="Screenshot 2026-10-25 174403" src="https://github.com/user-attachments/assets/b33d8cbd-dc82-47f4-b42f-60f72b908932" />


---

# Task 7 — (Optional) Update One Small Detail and Re-Upload

## Goal

Edit a small visible detail, re-upload it to S3, and confirm the change appears live.

### Evidence

#### Screenshot 7 (optional) — Before and after views, or a browser view showing the updated text

<img width="567" height="213" alt="Screenshot 2026-10-25 182415" src="https://github.com/user-attachments/assets/6c3a64ac-e6a3-41de-a96b-77104f4071f2" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Include the live S3 Website Endpoint URL
- Do not expose sensitive AWS account information

---

# Completion Checklist

- [ ] Task 1: Template downloaded/cloned with `index.html` confirmed (Screenshot 1)
- [ ] Task 2: Globally unique S3 bucket created (Screenshot 2)
- [ ] Task 3: Website files uploaded with `index.html` at bucket root (Screenshot 3)
- [ ] Task 4: Static website hosting enabled (Screenshot 4)
- [ ] Task 5: Public-read bucket policy saved (Screenshot 5)
- [ ] Task 6: Live website verified through the S3 website endpoint (Screenshot 6)
- [ ] Task 7: Optional small update re-uploaded and verified (Screenshot 7)
- [ ] S3 Website Endpoint URL included
- [ ] No sensitive account information exposed

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
