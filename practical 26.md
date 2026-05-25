
---
# **Cracking a Password-Protected Microsoft Word Document Using John the Ripper on Kali Linux**

## Objective
The objective of this practical is to use John the Ripper to crack a password hash extracted from a Microsoft Word document (.docx) on Kali Linux.

---
## Pre-requisites
1. **Kali Linux**: Ensure you have Kali Linux installed and running.
2. **John the Ripper**: Ensure John the Ripper is installed on your system.
3. **Python**: Ensure Python is installed, as `office2john.py` is a Python script.
4. **Sample Document**: Have a sample Microsoft Word document (.docx) with a password-protected file.

---
## Commands as Steps

1. **Check the Manual for John the Ripper**
   ```bash
   man john
   ```
   **Explanation**: This command displays the manual page for John the Ripper, providing detailed information about its usage, options, and examples.

2. **Locate the `office2john` Script**
   ```bash
   locate office2john
   ```
   **Explanation**: This command searches for the `office2john` script, which is used to extract password hashes from Microsoft Office documents. The script is typically located in the `/usr/share/john/` directory.

3. **Extract the Password Hash**
   ```bash
   /usr/share/john/office2john.py /root/Desktop/hash.docx > mydoc.txt
   ```
   **Explanation**: This command uses the `office2john.py` script to extract the password hash from the `hash.docx` file located on the desktop. The extracted hash is then saved to a file named `mydoc.txt`.

4. **View the Extracted Hash**
   ```bash
   cat mydoc.txt
   ```
   **Explanation**: This command displays the contents of `mydoc.txt`, which should contain the extracted password hash.

5. **Check John the Ripper Help**
   ```bash
   john -h
   ```
   **Explanation**: This command displays the help information for John the Ripper, providing details about the various options and commands available.

6. **Crack the Password Hash**
   ```bash
   john mydoc.txt --length=6
   ```
   **Explanation**: This command instructs John the Ripper to attempt to crack the password hash stored in `mydoc.txt`. The `--length=6` option specifies that the password is 6 characters long, which can help narrow down the search space and speed up the cracking process.

---
## Additional Notes
- **Password Length**: Adjust the `--length` option based on the expected length of the password. If you are unsure, you can omit this option, and John the Ripper will attempt to crack the password without any length restrictions.
- **Wordlist**: You can specify a wordlist using the `--wordlist` option if you have a specific list of potential passwords.
- **Cracking Time**: The time it takes to crack the password depends on the complexity of the password and the computational power of your system.
