# Assignment 4 — Deploy EpicReads Portfolio Website via Nginx

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will deploy a static portfolio website on an Ubuntu VM using Nginx. You will download the website template, add your ownership proof in the footer, deploy the files to the Nginx web root, and verify the website is publicly accessible via a browser.

---

# Task 0 — Pre-flight Check

## Goal

Verify the Ubuntu VM and Nginx are ready for deployment.

### Evidence

#### Screenshot 0 — Output of `sudo systemctl status nginx --no-pager` showing Active (running)

<img width="1349" height="679" alt="Screenshot 2026-09-27 202254" src="https://github.com/user-attachments/assets/a915618b-5726-49a3-95e7-0b240125ab15" />


---

# Task 1 — Get the Website Source Code

## Goal

Download and extract the portfolio website template.

### Evidence

#### Screenshot 1 — Output of `ls -la` showing the extracted project folder

<img width="1364" height="714" alt="Screenshot 2026-09-27 202635" src="https://github.com/user-attachments/assets/782a9ee2-103c-4e03-8d7b-3eea5c13d370" />


---

# Task 2 — Add Ownership Proof (Anti-Copy Change)

## Goal

Update the website footer with your deployment details.

### Evidence

#### Screenshot 2 — Nano editor open with the updated footer showing your Full Name, Group, Week, and Date

<img width="1095" height="164" alt="Screenshot 2026-09-27 211929" src="https://github.com/user-attachments/assets/5dc1d4d5-0d81-45d8-bdd2-e9b2d3c81077" />


---

# Task 3 — Deploy Website via Nginx

## Goal

Deploy the portfolio website to the Nginx web root.

### Evidence

#### Screenshot 3 — Output of `sudo nginx -t` showing configuration test successful

<img width="865" height="90" alt="Screenshot 2026-09-28 090510" src="https://github.com/user-attachments/assets/360c40b7-c89e-4e05-b31d-cdcad3b37cd0" />


---

#### Screenshot 4 — Output of `ls /var/www/html` showing deployed website files

<img width="872" height="66" alt="Screenshot 2026-09-28 090621" src="https://github.com/user-attachments/assets/5d2adfd6-e1ba-4569-8837-ae90657270d4" />


---

# Task 4 — Verify Website is Live

## Goal

Verify the deployed website is publicly accessible and the footer contains your details.

### Evidence

#### Screenshot 5 — Output of `curl ifconfig.me` showing the server's public IP address

<img width="872" height="66" alt="Screenshot 2026-09-28 090621" src="https://github.com/user-attachments/assets/c521b4f2-8436-4001-bea5-d8bb57b71321" />


---

#### Screenshot 6 — Browser showing the live website with your Full Name and deployment details in the footer

<img width="833" height="449" alt="Screenshot 2026-09-28 092743" src="https://github.com/user-attachments/assets/61c72cd2-9143-4fda-85ee-eaed2ec00606" />


---

# Task 5 — Mini Real DevOps Operational Check

## Goal

Verify the deployed website and Nginx service are healthy.

### Evidence

#### Screenshot 7 — Output of `systemctl is-enabled nginx`

<img width="955" height="72" alt="Screenshot 2026-09-28 093231" src="https://github.com/user-attachments/assets/f5cbd009-3d1b-4e01-81af-8408ce3c89bf" />


---

#### Screenshot 8 — Output of `curl -I http://localhost` showing 200 OK

<img width="891" height="197" alt="Screenshot 2026-09-28 093141" src="https://github.com/user-attachments/assets/27c71986-0d61-4818-b12a-3af9ee394f93" />


---

# LinkedIn Post (Mandatory)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dVeQZB6H

---

#### Screenshot — Published LinkedIn post showing the live website with your Full Name in the footer

<img width="1355" height="635" alt="Screenshot 2026-09-28 132722" src="https://github.com/user-attachments/assets/69cbb31b-7c51-4aa4-97d3-1d3710e32fa3" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Ownership proof in the footer is mandatory
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [✅] Screenshot 0: Nginx service status (active/running)
- [✅] Screenshot 1: Website files downloaded and extracted
- [✅] Screenshot 2: Footer updated with Full Name, Group, Week, and Date
- [✅] Screenshot 3: Nginx configuration test successful
- [✅] Screenshot 4: Website files deployed to /var/www/html
- [✅] Screenshot 5: Public IP retrieved
- [✅] Screenshot 6: Live website accessible in browser with footer details
- [✅] Screenshot 7: Nginx enabled on boot
- [✅] Screenshot 8: Local HTTP response returns 200 OK
- [✅] LinkedIn post published and URL submitted
- [✅] Full Name visible in all required screenshots
- [✅] No sensitive data exposed

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
