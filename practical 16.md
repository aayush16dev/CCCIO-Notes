
---

# **CUPP {Common user password profiler}**
## **Overview**

CUPP is a powerful wordlist generation tool available in Kali Linux.  
It creates **highly targeted and realistic password lists** by using personal information of the target user such as name, hobbies, dates, relationships, and interests.  
This method greatly improves the success rate of password cracking while reducing manual effort.

---

## **Key Components**

### **1. User Information Gathering**

CUPP collects details such as:

- **Personal Information**  
    Name, date of birth, age, location, hometown, nicknames
- **Professional Information**  
    Job title, company, school, college
- **Interests**  
    Hobbies, sports, music, movies, books
- **Relationships**  
    Spouse, children, friends, pets

### **2. Word List Generation Techniques**

CUPP creates passwords using:

- **Simple Transformations** — direct use of provided data
- **Common Variations** — adding numbers, symbols, prefixes, suffixes
- **Combinations** — mixing multiple pieces of information
- **Rule‑Based Modifications** — applying common password patterns

---

## **Step-by-Step Procedure**

### **1. Gather User Information**

Collect as much information as possible about the target user.  
More information → better and stronger wordlist.

---

### **2. Run CUPP**

Open terminal in Kali Linux and run:

```bash
cupp -i
```

**Options:**

- `-i` → Interactive mode

Follow the on‑screen questions and enter the user’s details.

---

### **3. Review and Improve Wordlist**

Open the generated file:

```bash
cat output_file.txt
```

- Add any missing variations
- Remove unrealistic entries if required
- Combine with other wordlists for stronger results

---

### **4. Use Wordlist for Password Cracking**

The generated wordlist can now be used with tools such as:

- **John the Ripper**
- **Hydra**
- **Hashcat**

---

## **Example**

```bash
cupp -i -o john.txt
```

Creates a customized password list named **john.txt**.

---

## **Key Points**

- Highly effective for **targeted password attacks**
- Saves time compared to manual wordlist creation
- Must be used **only with proper authorization**
- Useful for **penetration testing & security assessments**

---](<Below is a **rewritten, exam-ready practical record** based strictly on the commands, outputs, and workflow you executed.
Language is formal, step-wise, and suitable for **cybersecurity lab files / practical journals**.

---

# Practical: CUPP – Common User Password Profiler

## Aim

To study and perform targeted password wordlist generation using **CUPP (Common User Password Profiler)** in Kali Linux through interactive profiling, existing wordlist enhancement, dictionary download, and default credential extraction.

---

## Tool Used

* **CUPP (cupp.py)**
* Platform: **Kali Linux**

---

## Overview

CUPP is a password profiling tool that generates customized wordlists based on user-specific information such as names, dates, relationships, pets, and organizations.
It supports multiple operational modes including interactive profiling, improving existing wordlists, downloading large dictionaries, and extracting default credentials from known databases.

---

## Command Usage and Options

```bash
cupp [-h] [-i | -w FILENAME | -l | -a | -v] [-q]
```

### Important Options

* `-i` : Interactive user profiling
* `-w` : Improve an existing wordlist
* `-l` : Download large public wordlists
* `-a` : Extract default usernames/passwords from Alecto DB
* `-v` : Show version
* `-q` : Quiet mode

---

## Practical Procedure

### 1. Interactive Mode (User Profiling)

**Command executed:**

```bash
cupp -i
```

**Observation:**

* CUPP launches in interactive mode.
* Syntax warnings related to escape sequences are displayed but do **not affect execution**.
* User is prompted to enter victim-specific information.

**Data Entered:**

* First Name: Aayush
* Surname: Saxena
* Nickname: ark
* Birthdate: 16102004
* Partner Name/Nickname/Birthdate
* Child Name/Nickname/Birthdate
* Pet Name
* Company Name
* Leet mode enabled (1337)

**Result:**

```text
[+] Saving dictionary to aayush.txt
[+] Total words generated: 10058
```

**Output File Generated:**

```bash
aayush.txt
```

This file contains a highly targeted password list based on the provided information.

---

### 2. Improving an Existing Wordlist

**Command executed:**

```bash
cupp -w /root/Desktop/tool/wrdlst.txt
```

**Selected Options:**

* Concatenate words: Yes
* Add special characters: Yes
* Add random numbers: Yes
* Leet mode: Default

**Result:**

```text
[+] Saving dictionary to wrdlst.txt.cupp.txt
[+] Total words generated: 17303
```

**Output File Generated:**

```bash
wrdlst.txt.cupp.txt
```

This process expands an existing wordlist using CUPP’s transformation rules.

---

### 3. Downloading Public Wordlists

**Command executed:**

```bash
cupp -l
```

**Action:**

* User selects dictionary category **Hindi (Option 16)**.
* CUPP downloads the compressed wordlist from the public FTP repository.

**Result:**

```text
[+] files saved to dictionaries/hindi/
```

**Directory Created:**

```bash
dictionaries/hindi/
```

This feature provides large language-specific wordlists for broad password attacks.

---

### 4. Extracting Default Credentials (Alecto DB)

**Command executed:**

```bash
cupp -a
```

**Action:**

* CUPP checks for Alecto database.
* Downloads `alectodb.csv.gz`.
* Extracts default usernames and passwords.

**Resulting Files:**

```bash
alectodb-usernames.txt
alectodb-passwords.txt
```

These files contain commonly used credentials collected from public breach databases.

---

## Files Generated During Experiment

| File Name                | Description                    |
| ------------------------ | ------------------------------ |
| `aayush.txt`             | Custom user-profiled wordlist  |
| `wrdlst.txt.cupp.txt`    | Enhanced wordlist              |
| `alectodb-usernames.txt` | Default usernames              |
| `alectodb-passwords.txt` | Default passwords              |
| `dictionaries/`          | Downloaded public dictionaries |

---

## Applications

The generated wordlists can be used with password-cracking tools such as:

* John the Ripper
* Hashcat
* Hydra

---
