# Assignment 3 — Production Maintenance Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will treat your already deployed React application (on Ubuntu VM with Nginx) as a live production system. You will perform structured operational checks covering network validation, service health, log analysis, resource monitoring, configuration verification, and incident simulation with recovery — mirroring real on-call DevOps responsibilities.

---

# Task 1 — Server Access & Networking Validation

## Goal

Verify that the deployed React application is reachable from the browser and confirm basic network connectivity of the Ubuntu VM.

### Evidence

#### Screenshot 1 — Browser showing the React app with your Full Name visible on the UI

<img width="835" height="446" alt="image" src="https://github.com/user-attachments/assets/bf903bcb-45cd-4e1a-b034-ea3c405ee2e6" />


---

#### Screenshot 2 — Output of `ip a`

<img width="1348" height="471" alt="Screenshot 2026-09-27 184406" src="https://github.com/user-attachments/assets/55173125-7803-4fc3-9a4a-18471ea457b4" />


---

#### Screenshot 3 — Output of `sudo ss -tulpen`

<img width="1362" height="714" alt="Screenshot 2026-09-27 184535" src="https://github.com/user-attachments/assets/d3bb6fa6-0522-486a-859b-b73d92888f39" />


---

#### Screenshot 4 — Output of `sudo ufw status`

<img width="1361" height="714" alt="Screenshot 2026-09-27 185413" src="https://github.com/user-attachments/assets/9de97476-d13c-4f70-b5cf-4041c887289f" />


---

### Notes

Answer the following in your own words:

**1. What proves Nginx is listening on 0.0.0.0:80?**

The output of sudo ss -tulpen shows LISTEN on 0.0.0.0:80, which confirms that the Nginx web server is actively listening for HTTP connections on port 80.

---

**2. What proves SSH is active on port 22?**

The sudo ss -tulpen output includes LISTEN on 0.0.0.0:22, showing that the SSH service is running and accepting connections on port 22.

---

**3. Did you find any unexpected open ports? Explain briefly.**

Yes. Besides ports 22 (SSH) and 80 (Nginx), ports 631 (CUPS printing service) and 3000 (Node.js development server) were also open. These are common development services, but they should be disabled in production if they are not needed.

---

# Task 2 — Service Health & Systemd Validation (Nginx)

## Goal

Verify that Nginx is properly installed, running, enabled at boot, and safely configured.

### Evidence

#### Screenshot 1 — Output of `systemctl status nginx --no-pager`

<img width="968" height="333" alt="Screenshot 2026-09-27 190141" src="https://github.com/user-attachments/assets/a8e8babd-c79b-4a53-9e22-8c8b862d1096" />


---

#### Screenshot 2 — Output of `sudo nginx -t`

<img width="1121" height="134" alt="Screenshot 2026-09-27 190539" src="https://github.com/user-attachments/assets/42591c69-0419-499c-b8b1-a4089d2bd021" />


---

#### Screenshot 3 — Output of `sudo ss -lptn '( sport = :80 )'`

<img width="1173" height="273" alt="Screenshot 2026-09-27 190612" src="https://github.com/user-attachments/assets/133b3738-ae38-42f2-bea4-facbccb3f78e" />


---

### Notes

Answer the following in your own words:

**1. What happens if Nginx fails to restart in production?**

If Nginx fails to restart, the website becomes unavailable and users may receive connection errors or a 502/503 response. This can cause downtime until the configuration or service issue is fixed.

---

**2. What's your basic rollback plan?**

My rollback plan is to restore the last working Nginx configuration, test it with sudo nginx -t, and restart the service. If the issue was caused by a new deployment, I would also restore the previous build files in /var/www/html to bring the application back online.

---

# Task 3 — Logs & Request Trace

## Goal

Verify real traffic flow and analyze logs to understand system behavior and errors.

### Evidence

#### Screenshot 1 — Output of `sudo tail -n 30 /var/log/nginx/access.log`

<img width="802" height="37" alt="Screenshot 2026-09-27 191636" src="https://github.com/user-attachments/assets/9ac0a0a6-4136-41f3-b170-98e670ca6652" />


---

#### Screenshot 2 — Output of `sudo tail -n 30 /var/log/nginx/error.log`

<img width="839" height="40" alt="Screenshot 2026-09-27 191653" src="https://github.com/user-attachments/assets/f9a0e20c-58ec-4d0d-ad9c-07a78f9a181a" />


---

#### Screenshot 3 — Output of `sudo journalctl -u nginx --no-pager -n 50`

<img width="1005" height="499" alt="Screenshot 2026-09-27 191735" src="https://github.com/user-attachments/assets/d463d16b-9379-4ccc-bb51-5bf2aebb63d8" />


---

### Notes

Answer the following in your own words:

**1. Were there any errors in the logs?**

- If yes, mention 1–2 example error lines from the logs and explain what each one means in simple terms.
- If no, explain what it means if the error log is empty or shows no recent errors during your check.

No. 
During my check, the Nginx error log showed no recent errors. This means Nginx did not report any configuration, startup, or request-processing issues while serving the React application.

---

**2. If there were no errors, what does that indicate about the system?**

It indicates that the system is healthy and stable. Nginx is running correctly, the configuration is valid, and the React application is being served without any detected server-side errors.

---

**3. Based on the access logs, were your curl requests visible in the log entries? What does that prove about traffic flow?**

Yes.
The curl requests appeared in the Nginx access log as HTTP GET requests. This proves that the requests successfully reached the Nginx server and were processed correctly, confirming end-to-end traffic flow between the client and the web server.

---

# Task 4 — System Resource Health Check (Capacity Red Flags)

## Goal

Assess server capacity and detect potential performance or failure risks.

### Evidence

#### Screenshot 1 — Output of `uptime`

<img width="585" height="43" alt="Screenshot 2026-09-27 192557" src="https://github.com/user-attachments/assets/f1763f9f-130b-4629-9bcf-cf9ce7120010" />


---

#### Screenshot 2 — Output of `free -h`

<img width="717" height="77" alt="Screenshot 2026-09-27 192609" src="https://github.com/user-attachments/assets/affd5791-3c1c-469e-bccb-6ed692dc4f3f" />


---

#### Screenshot 3 — Output of `df -h`

<img width="759" height="416" alt="Screenshot 2026-09-27 192646" src="https://github.com/user-attachments/assets/22edd8b2-6c14-45e8-8bb8-1e3ad9343aa2" />


---

#### Screenshot 4 — Output of `sudo du -sh /var/* | sort -h`

<img width="721" height="284" alt="Screenshot 2026-09-27 192704" src="https://github.com/user-attachments/assets/4cd9111b-4e81-44c7-b159-cb6e6671231d" />


---

### Notes

Answer the following in your own words:

**1. Which resource looks most critical right now? (CPU/load, memory, or disk) Explain why.**

disk space is the most critical resource when high because running completely out of storage causes immediate system-wide crashes, whereas high CPU or memory usually just degrades performance.

---

**2. What happens if disk becomes 100% full in a production server?**

Applications and databases crash when write transactions or logs fail, log files stop recording, temporary files cannot be created, and users may be locked out of SSH sessions—frequently resulting in data corruption and downtime.

---

# Task 5 — Configuration & Deployment Verification

## Goal

Ensure the correct React build is deployed and Nginx is serving it properly.

### Evidence

#### Screenshot 1 — Output of `ls -lah /var/www/html | head -n 20`

<img width="756" height="245" alt="Screenshot 2026-09-27 193442" src="https://github.com/user-attachments/assets/b0f13b10-c720-4d3f-8a16-f8370e3e9ef5" />


---

#### Screenshot 2 — Output of `grep -R "Deployed by" -n /var/www/html 2>/dev/null | head`

<img width="1355" height="685" alt="Screenshot 2026-09-27 193736" src="https://github.com/user-attachments/assets/8492dee6-59c7-4020-8b22-66fb26db9aaa" />


---

#### Screenshot 3 — Output of `grep -n "try_files" /etc/nginx/sites-available/default`

<img width="950" height="35" alt="Screenshot 2026-09-27 193833" src="https://github.com/user-attachments/assets/7e7ca4bc-1525-42b2-b2ed-892f115481f4" />


---

### Notes

Answer the following in your own words:

**1. How do you confirm that the correct version of the application is deployed?**

I confirm the deployment by opening the React application in the browser and verifying that it displays my full name (Gatadi Nagajyothi) and the current date (27 September 2026). I also ensure the production build has been copied to /var/www/html and is being served by Nginx.

---

# Task 6 — Nginx Configuration Failure Simulation

## Goal

Simulate a real-world Nginx misconfiguration and recover the service safely.

### Evidence

#### Screenshot 1 — Output of `sudo nginx -t` showing the syntax error (broken config)

<img width="950" height="35" alt="Screenshot 2026-09-27 193833" src="https://github.com/user-attachments/assets/3d67ecd0-a333-4b52-9daf-aa3c5ab755ad" />


---

#### Screenshot 2 — Output of `sudo nginx -t` showing syntax ok (fixed config)

<img width="687" height="57" alt="Screenshot 2026-09-27 195632" src="https://github.com/user-attachments/assets/23cc10f3-647d-4e26-9ad3-75c39b8e2c01" />


---

#### Screenshot 3 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

<img width="749" height="228" alt="Screenshot 2026-09-27 195654" src="https://github.com/user-attachments/assets/11b1ef3f-41d8-49e0-bbfa-2066d7d25a60" />


---

### Notes

Answer the following in your own words:

**1. What caused the configuration failure?**

The configuration failed because the semicolon (;) was removed from the try_files $uri /index.html; directive. This created a syntax error, so sudo nginx -t failed.

---

**2. How did you fix the issue?**

I edited the Nginx configuration file, re-added the missing semicolon, saved the file, verified it with sudo nginx -t, and restarted Nginx using sudo systemctl restart nginx.

---

**3. How can you avoid this kind of issue in real production systems?**

Always validate configuration changes with nginx -t before restarting the service, review changes carefully, and keep a backup of the last working configuration so it can be restored quickly if needed.

---

# Task 7 — Web Application Failure Simulation

## Goal

Simulate missing deployment content and recover the application safely.

### Evidence

#### Screenshot 1 — Output of `curl -I http://<public-ip>` showing failure (non-200 response)

<img width="790" height="242" alt="Screenshot 2026-09-27 200528" src="https://github.com/user-attachments/assets/0890a6ee-4d24-4efc-9b8b-be8350b5b1bd" />


---

#### Screenshot 2 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

<img width="930" height="271" alt="Screenshot 2026-09-27 200542" src="https://github.com/user-attachments/assets/52ca3462-9da8-41b7-948f-b77484a974f3" />


---

### Notes

Answer the following in your own words:

**1. What caused the application to break in this scenario?**

The application broke because the semicolon (;) was removed from the try_files $uri /index.html; line in the Nginx configuration. This caused a syntax error, so Nginx could not validate the configuration.

---

**2. How did you fix the issue and restore the application?**

I opened the Nginx configuration file, re-added the missing semicolon, saved the file, verified it with sudo nginx -t, and restarted Nginx using sudo systemctl restart nginx. The application was restored successfully.

---

**3. What steps would you take to prevent this kind of issue in real production systems?**

I would always test configuration changes with nginx -t before restarting, keep a backup of the last working configuration, and use version control so changes can be reviewed and rolled back quickly if needed.

---

# Task 8 — Security & Reliability Review

## Goal

Review and reflect on the security and reliability practices applied during this assignment.

### Security & Reliability Notes

Answer the following in your own words:

**1. Why is SSH key-based authentication more secure than sharing passwords?**

SSH key-based authentication is more secure because it uses a unique cryptographic key instead of a password. Private keys are much harder to guess or steal, reducing the risk of unauthorized access.

---

**2. Why should only required ports be open on a production server?**

Only required ports should be open to reduce the server's attack surface. Closing unused ports helps prevent unauthorized access and improves overall system security.

---

**3. Why is it important for Nginx to be enabled on boot?**

Enabling Nginx on boot ensures the web server starts automatically whenever the server restarts. This improves reliability and keeps the application available without manual intervention.

---

**4. What are the risks of sharing secrets, keys, or credentials publicly?**

Sharing secrets or credentials can allow attackers to access servers, cloud accounts, or applications. It may lead to data breaches, unauthorized changes, and financial or security losses.

---

**5. Why should cloud resources be stopped or terminated when they are no longer needed?**

Stopping or terminating unused cloud resources prevents unnecessary costs and reduces security risks by removing idle services that could be exposed to attacks.

---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dCjiEnFY

---

#### Screenshot — Published LinkedIn post

<img width="1358" height="626" alt="Screenshot 2026-09-27 201647" src="https://github.com/user-attachments/assets/79d3c540-c963-4ae3-a547-5824a70ef4b4" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [✅] Task 1: Screenshots (browser, ip a, ss -tulpen, ufw status) + Notes answered
- [✅] Task 2: Screenshots (nginx status, nginx -t, ss port 80) + Notes answered
- [✅] Task 3: Screenshots (access log, error log, journalctl) + Notes answered
- [✅] Task 4: Screenshots (uptime, free -h, df -h, du -sh) + Notes answered
- [✅] Task 5: Screenshots (ls html, grep deployed by, grep try_files) + Notes answered
- [✅] Task 6: Screenshots (nginx -t fail, nginx -t pass, curl recovery) + Notes answered
- [✅] Task 7: Screenshots (curl failure, curl recovery) + Notes answered
- [✅] Task 8: Security & Reliability Notes answered
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
