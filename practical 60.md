
---
# Practical Guide for Using CeWL in Kali Linux

CeWL is an OSINT and password profiling tool used in cybersecurity to generate custom wordlists from websites. It crawls web pages and extracts words that can later be used for password auditing, security assessments, and penetration testing in authorized environments.

---

# Objective

To understand the usage of CeWL for website crawling and custom wordlist generation in a controlled cybersecurity lab environment.

---

# Prerequisites

* Kali Linux or Debian-based Linux distribution
* Internet connectivity
* Basic understanding of Linux commands
* Basic knowledge of web crawling and password auditing

---

# Introduction to CeWL

CeWL stands for:

```text id="jlwm8n"
Custom Word List Generator
```

It is written in Ruby and is commonly used during:

* Password auditing
* Security assessments
* OSINT investigations
* Red team exercises
* Social engineering awareness testing

---

# Features of CeWL

* Website crawling
* Custom wordlist generation
* Metadata extraction
* Email extraction
* Recursive crawling
* Number inclusion
* Authentication support

---

# Step 1: View Help Menu

Open the terminal and run:

**Bash**

```bash id="jlwm6u"
cewl --help
```

or

```bash id="jlwm2d"
cewl -h
```

## **Explanation:**
Displays all available options and parameters.
### Output:

```
CeWL 6.2.1 (More Fixes) Robin Wood (robin@digi.ninja) (https://digi.ninja/)
Usage: cewl [OPTIONS] ... <url>

    OPTIONS:
        -h, --help: Show help.
        -k, --keep: Keep the downloaded file.
        -d <x>,--depth <x>: Depth to spider to, default 2.
        -m, --min_word_length: Minimum word length, default 3.
        -x, --max_word_length: Maximum word length, default unset.
        -o, --offsite: Let the spider visit other sites.
        --exclude: A file containing a list of paths to exclude
        --allowed: A regex pattern that path must match to be followed
        -w, --write: Write the output to the file.
        -u, --ua <agent>: User agent to send.
        -n, --no-words: Don't output the wordlist.
        -g <x>, --groups <x>: Return groups of words as well
        --lowercase: Lowercase all parsed words
        --with-numbers: Accept words with numbers in as well as just letters
        --convert-umlauts: Convert common ISO-8859-1 (Latin-1) umlauts (ä-ae, ö-oe, ü-ue, ß-ss)
        -a, --meta: include meta data.
        --meta_file file: Output file for meta data.
        -e, --email: Include email addresses.
        --email_file <file>: Output file for email addresses.
        --meta-temp-dir <dir>: The temporary directory used by exiftool when parsing files, default /tmp.
        -c, --count: Show the count for each word found.
        -v, --verbose: Verbose.
        --debug: Extra debug information.

        Authentication
        --auth_type: Digest or basic.
        --auth_user: Authentication username.
        --auth_pass: Authentication password.

        Proxy Support
        --proxy_host: Proxy host.
        --proxy_port: Proxy port, default 8080.
        --proxy_username: Username for proxy, if required.
        --proxy_password: Password for proxy, if required.

        Headers
        --header, -H: In format name:value - can pass multiple.

    <url>: The site to spider.

```

---

# Step 2: Generate a Basic Wordlist

**Bash**

```bash id="jlwm0s"
cewl http://demo.testfire.net/ -w data.txt
```

### Parameters

| Parameter | Meaning             |
| --------- | ------------------- |
| `-w`      | Save output to file |

**Explanation:**
Crawls the target website and stores extracted words inside `data.txt`.

---

# Step 3: Generate Lowercase Wordlist

**Bash**

```bash id="jlwm4z"
cewl http://demo.testfire.net/ --lowercase -w data1.txt
```

**Explanation:**
Converts all extracted words into lowercase before saving.

---

# Step 4: Set Crawl Depth

**Bash**

```bash id="jlwm7x"
cewl http://demo.testfire.net/ -d 2 -w data2.txt
```

### Parameter

| Parameter | Meaning                   |
| --------- | ------------------------- |
| `-d 2`    | Crawl up to depth level 2 |

**Explanation:**
Allows CeWL to recursively crawl linked pages up to two levels deep.

---
# Step 5: Extract Email Addresses

**Bash**

```bash id="jlwm9t"
cewl http://demo.testfire.net/ -e
```

**Explanation:**
Extracts email addresses discovered during crawling.

---

# Step 6: Save Emails and Words

**Bash**

```bash id="wjlwm1"
cewl https://testaspnet.vulnweb.com/ -e -w data3.txt
```

### Parameters

| Parameter | Meaning            |
| --------- | ------------------ |
| `-e`      | Extract emails     |
| `-w`      | Save words to file |

---

# Step 7: Extract Metadata

**Bash**

```bash id="jlwm5n"
cewl http://demo.testfire.net/ --meta
```

**Explanation:**
Extracts metadata such as document authors and additional page information.

---

# Step 8: Verbose Mode

**Bash**

```bash id="jlwm3p"
cewl http://demo.testfire.net/ -v -w test.txt
```

### Parameter

| Parameter | Meaning      |
| --------- | ------------ |
| `-v`      | Verbose mode |

**Explanation:**
Displays detailed crawling activity.

---

# Step 9: Count Word Occurrences

**Bash**

```bash id="jlwm2k"
cewl http://demo.testfire.net/ -c | more
```

### Parameter

| Parameter | Meaning         |
| --------- | --------------- |
| `-c`      | Show word count |

**Explanation:**
Displays extracted words along with frequency counts.

---

# Step 10: Minimum Word Length

**Bash**

```bash id="wjglwm"
cewl http://demo.testfire.net/ -m 5 -w test2.txt
```

### Parameter

| Parameter | Meaning               |
| --------- | --------------------- |
| `-m 5`    | Minimum word length 5 |

**Explanation:**
Filters out words shorter than 5 characters.

---

# Step 11: Include Numbers

**Bash**

```bash id="jlwm44"
cewl http://demo.testfire.net/ --with-numbers -w test1.txt
```

**Explanation:**
Includes words containing numeric characters.

---

# Step 12: Display Emails Without Wordlist

**Bash**

```bash id="jlwm66"
cewl http://demo.testfire.net/ -n -e
```

### Parameters

| Parameter | Meaning                |
| --------- | ---------------------- |
| `-n`      | Do not output wordlist |
| `-e`      | Extract emails         |

---

# Step 13: Authentication Support

CeWL supports crawling password-protected websites.

**Bash**

```bash id="jlwm11"
cewl http://demo.testfire.net/login.jsp --auth_type basic --auth_user test --auth_pass test -w file.txt
```

### Parameters

| Parameter     | Meaning             |
| ------------- | ------------------- |
| `--auth_type` | Authentication type |
| `--auth_user` | Username            |
| `--auth_pass` | Password            |

**Explanation:**
Uses HTTP Basic Authentication to crawl protected pages.

---

# Applications of CeWL

* Password auditing
* Wordlist generation
* OSINT investigations
* Security testing
* Red team assessments
* Cybersecurity training

---

