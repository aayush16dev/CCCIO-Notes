

---

# **Using Name-That-Hash in Kali Linux**

## Objective

The objective of this practical is to use the **Name-That-Hash** tool in Kali Linux to identify different types of cryptographic hashes instantly.

---

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Python Installed**: Required to run the tool.

3. **Internet Connectivity**: Needed to download the repository from GitHub.

4. **Terminal Access**: Required to execute commands.

5. **Basic Knowledge of Hashing**: Understanding of common hash algorithms.

---

# Commands as Steps

## 1. Clone the Name-That-Hash Repository

```bash id="m7v2qx"
git clone https://github.com/hashpals/name-that-hash.git

cd name-that-hash
```

### Explanation

Downloads the Name-That-Hash project from GitHub and navigates into the project directory.

---

## 2. Install Required Dependencies

```bash id="k4n9pw"
pip install -r requirements.txt
```

### Explanation

Installs all Python dependencies required for the tool to function correctly.

---

## 3. Identify a Hash Using Text Input

```bash id="t8r3uy"
nth --text '5f4dcc3b5aa765d61d8327deb882cf99'
```

### Explanation

Identifies the possible hash type of the provided hash value.

> Note: Use single quotes `' '` instead of double quotes `" "` in Linux terminals.

---

## 4. Identify Hashes from a File

```bash id="x1p6mq"
nth --file hash
```

### Explanation

Checks all hashes stored in the specified file.

The file should contain one hash per line.

---

## 5. Display Output in JSON Format

```bash id="v5d8kn"
nth --text '5f4dcc3b5aa765d61d8327deb882cf99' --greppable
```

### Explanation

Displays the identified hash information in JSON format, useful for parsing or grep operations.

---

## 6. Enable Base64 Decoding

```bash id="n2u7yb"
nth --text 'NWY0ZGNjM2I1YWE3NjVkNjFkODMyN2RlYjg4MmNmOTk=' --base64
```

### Explanation

Attempts Base64 decoding before identifying the hash type.

---

## 7. Search for Hashes Within a String

```bash id="q9m4rc"
nth --text 'User hash: 5f4dcc3b5aa765d61d8327deb882cf99' --extreme
```

### Explanation

Extracts and identifies hashes embedded inside larger text strings.

---

## 8. Run in Accessible Mode

```bash id="p3x8dt"
nth --text '5f4dcc3b5aa765d61d8327deb882cf99' --accessible
```

### Explanation

Runs the tool in accessible mode without ASCII art output.

---

## 9. Disable Banner Output

```bash id="y6k1vn"
nth --text '5f4dcc3b5aa765d61d8327deb882cf99' --no-banner
```

### Explanation

Runs the tool without displaying the startup banner.

---

## 10. Enable Verbose Logging

```bash id="w4t9ph"
nth --text '5f4dcc3b5aa765d61d8327deb882cf99' -v
```

### Explanation

Enables debugging logs for detailed execution information.

---

## 11. View Help Menu

```bash id="f8n2qa"
nth --help
```

### Explanation

Displays all available options and command usage details.

---

# Options

| Option                  | Description                          |
| ----------------------- | ------------------------------------ |
| `--help`                | Displays the help menu               |
| `-t`, `--text TEXT`     | Checks a single hash                 |
| `-f`, `--file FILENAME` | Checks hashes from a file            |
| `-g`, `--greppable`     | Outputs results in JSON format       |
| `-b64`, `--base64`      | Decodes Base64 before identification |
| `-a`, `--accessible`    | Enables accessible mode              |
| `-e`, `--extreme`       | Extracts hashes from strings         |
| `--no-banner`           | Removes startup banner               |
| `--no-john`             | Disables John The Ripper information |
| `--no-hashcat`          | Disables Hashcat information         |
| `-v`, `--verbose`       | Enables verbose debugging logs       |

---

