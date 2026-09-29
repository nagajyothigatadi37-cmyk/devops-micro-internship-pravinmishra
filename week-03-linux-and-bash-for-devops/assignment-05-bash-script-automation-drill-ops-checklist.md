# Assignment 5 — Bash Script Automation Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will practice Bash scripting by building a series of small automation scripts covering environment setup, variables, arrays, loops, file conditionals, if-else logic, and functions. These scripts form the foundation of real-world Linux automation used in DevOps, cloud, and production support environments.

---

# Task 1 — Bash Environment & Workspace Setup

## Goal

Verify that Bash is available on your system and create a clean workspace for this assignment.

### Evidence

#### Screenshot 1 — Output of `echo $SHELL` and `bash --version`

<img width="658" height="174" alt="Screenshot 2026-09-28 155458" src="https://github.com/user-attachments/assets/b3b79311-9c55-42ce-9f46-eff5ac25a2e0" />


---

#### Screenshot 2 — Output of `pwd` and `ls -lah` showing the scripts directory

<img width="692" height="499" alt="Screenshot 2026-09-28 155540" src="https://github.com/user-attachments/assets/bfb1b259-7dbe-4887-a09b-bbf00acff8a6" />


---

### Notes

Answer the following in your own words:

**1. What is Bash?**

Bash (Bourne Again Shell) is a command-line shell and scripting language used to interact with the Linux operating system. It allows users to run commands, automate repetitive tasks, and create shell scripts.

---

**2. What is the difference between shell and Bash?**

A shell is a program that lets users communicate with the operating system through commands. Bash is one specific type of shell, and it is the most commonly used shell in Linux because it supports both command execution and scripting.

---

**3. Why is it important to confirm the Bash version before writing scripts?**

Confirming the Bash version ensures that your script is compatible with the features available on your system. Some commands and syntax work only in newer Bash versions, so checking the version helps avoid errors and improves portability.

---

# Task 2 — Your First Bash Script

## Goal

Create your first Bash script, make it executable, and run it from the terminal.

### Evidence

#### Screenshot 1 — Content of `first-script.sh`

<img width="1355" height="721" alt="Screenshot 2026-09-28 161515" src="https://github.com/user-attachments/assets/a9784bf3-2927-4f1d-9c79-19cf74d478ff" />


---

#### Screenshot 2 — Output of `./first-script.sh`

<img width="644" height="75" alt="Screenshot 2026-09-28 161615" src="https://github.com/user-attachments/assets/46341c0f-583c-4011-b691-6c9a17b05a92" />


---

#### Screenshot 3 — Output of `ls -l first-script.sh` showing executable permission

<img width="657" height="42" alt="Screenshot 2026-09-28 161642" src="https://github.com/user-attachments/assets/20cf1b5c-b970-457c-8c33-db10eefdbdfb" />


---

### Notes

Answer the following in your own words:

**1. What is the purpose of `#!/bin/bash`?**

#!/bin/bash is called a shebang. It tells the operating system to run the script using the Bash interpreter, ensuring the script executes with Bash.

---

**2. Why do we use `chmod +x` before running a script?**

chmod +x gives the script execute permission. Without it, the file cannot be run directly as a program.

---

**3. What is the difference between running a script using `./script.sh` and `bash script.sh`?**

./script.sh runs the script as an executable file and requires execute permission (chmod +x).

bash script.sh runs the script through the Bash interpreter and does not require execute permission.

---

# Task 3 — Variables: User Information Script

## Goal

Use variables to store and display user-related information.

### Evidence

#### Screenshot 1 — Content of `user-info.sh`

<img width="651" height="80" alt="Screenshot 2026-09-29 092345" src="https://github.com/user-attachments/assets/0b50799b-997f-4aad-908d-ba13ec025a09" />


---

#### Screenshot 2 — Output of `./user-info.sh`

<img width="683" height="119" alt="Screenshot 2026-09-29 092437" src="https://github.com/user-attachments/assets/d49cb6b2-9328-4e1c-b467-5be35410a58e" />


---

### Notes

Answer the following in your own words:

**1. What is a variable in Bash?**

A variable in Bash is a named place used to store a value such as text, numbers, or other information. It allows us to store data and use it later in a script.

---

**2. Why should we avoid spaces around the `=` sign when creating variables?**

In Bash, there must be no spaces around the = sign when assigning a value. Bash interprets spaces as separators between commands and arguments.

Example:
name="Nagajyothi"

---

**3. How do you access the value stored inside a Bash variable?**

We use the $ symbol before the variable name to access its stored value.
Example:
    name="Nagajyothi"
    echo $name
Output:
    Nagajyothi

---

# Task 4 — Arrays & Loops: Tools Checklist Script

## Goal

Use arrays and loops to print a checklist of tools used in Bash scripting.

### Evidence

#### Screenshot 1 — Content of `tools-checklist.sh`

<img width="1366" height="768" alt="Screenshot 2026-09-29 152134" src="https://github.com/user-attachments/assets/189561ad-c09f-4088-abe4-bf419e8c385a" />


---

#### Screenshot 2 — Output of `./tools-checklist.sh`

<img width="724" height="176" alt="Screenshot 2026-09-29 152637" src="https://github.com/user-attachments/assets/f55c2926-7129-48af-91c7-eb572c12f22a" />


---

### Notes

Answer the following in your own words:

**1. What is an array in Bash?**

An array in Bash is a variable that can store multiple values under one name. Each value can be accessed using its index.

---

**2. Why are arrays useful in scripts?**

Arrays are useful because they allow us to store and manage multiple related values together. This makes scripts easier to organize and reduces repeated code.

---

**3. What does `"${tools[@]}"` mean?**

"${tools[@]}" means all the values stored in the tools array. It allows the script to access each tool individually, especially when used with a for loop.

---

**4. What is the purpose of the `for` loop in this script?**

The for loop goes through each value in the tools array one by one. It then prints the name of each tool available for practice.

---

# Task 5 — Loops: Number Counter Script

## Goal

Use loops to repeat a task multiple times.

### Evidence

#### Screenshot 1 — Content of `counter.sh`

<img width="1364" height="718" alt="Screenshot 2026-09-29 154652" src="https://github.com/user-attachments/assets/45eda255-05ce-49f0-a153-d295aade1943" />


---

#### Screenshot 2 — Output of `./counter.sh`

<img width="620" height="167" alt="Screenshot 2026-09-29 155202" src="https://github.com/user-attachments/assets/44d45c2f-136a-4e7b-bd97-14ca4234c6ff" />


---

### Notes

Answer the following in your own words:

**1. What is a loop?**

A loop is a programming structure that repeats a set of commands multiple times until a specified condition is met.

---

**2. Why do we use loops in Bash scripting?**

We use loops to repeat tasks automatically without writing the same commands again and again. This makes scripts shorter and easier to manage.

---

**3. How many times did the loop run in your script?**

The loop ran 6 times because there are 6 tools in the tools array: bash, nano, chmod, echo, ls, and pwd.

---

**4. What would you change if you wanted the loop to run 10 times?**

I would change the loop so that it uses a range from 1 to 10, 
for example:
    for i in {1..10}
    do
       echo "Practice number: $i"
    done

---

# Task 6 — Files & Conditionals: File Validation Script

## Goal

Use file checks and conditionals to verify whether files and directories exist.

### Evidence

#### Screenshot 1 — Output of `ls -lah ../test-folder`

<img width="743" height="103" alt="Screenshot 2026-09-29 205707" src="https://github.com/user-attachments/assets/6627d3bc-1bf1-45be-8fa8-6e16dd762c83" />


---

#### Screenshot 2 — Content of `file-check.sh`

<img width="1364" height="690" alt="Screenshot 2026-09-29 205133" src="https://github.com/user-attachments/assets/30cf1487-5063-4ed5-a546-8c813cc8855c" />


---

#### Screenshot 3 — Output of `./file-check.sh`

<img width="683" height="126" alt="Screenshot 2026-09-29 205431" src="https://github.com/user-attachments/assets/448c466c-5651-46a9-be96-d0ad550a66e1" />


---

### Notes

Answer the following in your own words:

**1. What does `-d` check in Bash?**

The -d condition checks whether a given path exists and is a directory.

---

**2. What does `-f` check in Bash?**

The -f condition checks whether a given path exists and is a regular file.

---

**3. Why should file and directory paths be stored in variables?**

Storing paths in variables makes the script easier to read and modify. We can change the path in one place instead of changing it throughout the script.

---

**4. What happens if the file does not exist?**

If the file does not exist, the -f condition returns false. The script can then use an else statement to display a message such as "File does not exist."

---

# Task 7 — Conditionals: Pass or Retry Script

## Goal

Use if-else conditionals to make decisions based on a variable value.

### Evidence

#### Screenshot 1 — Content of `score-check.sh` with `score=85`

<img width="1358" height="716" alt="Screenshot 2026-09-29 210615" src="https://github.com/user-attachments/assets/944c68b0-cf39-4905-81fb-9bb4fb542e27" />


---

#### Screenshot 2 — Output showing `Result: Pass`

<img width="759" height="178" alt="Screenshot 2026-09-29 211557" src="https://github.com/user-attachments/assets/aadd3c43-3cbd-487c-a74b-80b25a39c82c" />


---

#### Screenshot 3 — Content of `score-check.sh` with `score=55`

<img width="1364" height="710" alt="Screenshot 2026-09-29 211423" src="https://github.com/user-attachments/assets/1391f771-4011-43a5-8869-b100b96a8d22" />


---

#### Screenshot 4 — Output showing `Result: Retry`

<img width="788" height="134" alt="Screenshot 2026-09-29 211737" src="https://github.com/user-attachments/assets/e9e20f07-6933-441a-8e48-38513a15536b" />


---

### Notes

Answer the following in your own words:

**1. What is the purpose of if-else in Bash?**

The if-else statement is used to make decisions in a Bash script. It runs one set of commands when a condition is true and another set when the condition is false.

---

**2. What does `-ge` mean?**

-ge means greater than or equal to. For example, [ "$score" -ge 70 ] checks whether the score is 70 or higher.

---

**3. Why should conditions be tested with different values?**

Conditions should be tested with different values to make sure the script works correctly in different situations. It helps find errors and unexpected results.

---

**4. How can conditionals help in automation scripts?**

Conditionals help automation scripts make decisions automatically. For example, a script can check a file, score, or system status and perform different actions based on the result.

---

# Task 8 — Functions: Final Bash Automation Script

## Goal

Create a final Bash script using functions to organize reusable code.

### Evidence

#### Screenshot 1 — Content of `final-automation.sh`

<img width="1365" height="720" alt="Screenshot 2026-09-29 212917" src="https://github.com/user-attachments/assets/82bdb90f-098f-489d-ac45-a3466b614deb" />

<img width="1363" height="719" alt="Screenshot 2026-09-29 213016" src="https://github.com/user-attachments/assets/0f9e9a58-fa28-46fc-a226-47b703eed1ab" />

---

#### Screenshot 2 — Output of `./final-automation.sh`

<img width="783" height="367" alt="Screenshot 2026-09-29 213203" src="https://github.com/user-attachments/assets/4f15a26e-98a2-477c-9d08-17d1ddc04751" />


---

#### Screenshot 3 — Output of `ls -lah` showing all created scripts

<img width="732" height="75" alt="Screenshot 2026-09-29 213247" src="https://github.com/user-attachments/assets/ce4db7ce-0adc-4e51-9925-f05d8308489b" />


---

### Notes

Answer the following in your own words:

**1. What is a function in Bash?**

Add your answer here.

---

**2. Why are functions useful in scripts?**

Add your answer here.

---

**3. Which functions did you create in this script?**

Add your answer here.

---

**4. How does this final script combine variables, arrays, loops, conditionals, files, and functions?**

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

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- All script files must be created and run successfully
- Required notes must be answered clearly for every task
- Do not expose sensitive information (keys, passwords, credentials)

---

# Completion Checklist

- [ ] Task 1: Environment setup verified, workspace created (Screenshots 1–2, Notes answered)
- [ ] Task 2: First script created, executed, permissions verified (Screenshots 1–3, Notes answered)
- [ ] Task 3: Variables script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 4: Arrays and loops script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 5: Counter loop script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 6: File validation script created and run (Screenshots 1–3, Notes answered)
- [ ] Task 7: Pass/Retry conditional script tested with both values (Screenshots 1–4, Notes answered)
- [ ] Task 8: Final automation script created and run (Screenshots 1–3, Notes answered)
- [ ] All scripts run without errors
- [ ] Full Name visible in all required screenshots
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
