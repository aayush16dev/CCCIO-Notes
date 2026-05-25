# CRUNCH
---
## **Overview**

Crunch is a password wordlist generator tool used in penetration testing and cybersecurity. It allows users to create custom wordlists tailored to specific requirements, making it more effective than generic wordlists.

---
## **Key Features and Functionalities**

1. **Basic Structure**
    
    - Command syntax: `Crunch <min> <max> <charset> -t <pattern> -o<filename>`
        
        - **Min**: Minimum password length
        - **Max**: Maximum password length
        - **Charset**: Optional character set for password generation
        - **Pattern**: Optional pattern for customization
        - **Filename**: File to save the wordlist
    - Example: `crunch 3 4 | more` (Generates passwords of lengths 3 to 4).
	
2. **Wordlist Compression**
    
    - Supports compression formats like `.gzip`, `.bzip2`, `.lzma`, `.7z`.
    - Example: `crunch 4 4 -t %%%% -z gzip -o w2.txt`.
3. **Charset Customization**
    
    - Default charsets:
        - Lowercase: `a-z`
        - Uppercase: `A-Z`
        - Numbers: `0-9`
        - Symbols: `!@#$%^`
    - Example: `crunch 5 7 -f /usr/share/crunch/charset.lst mixalpha | more` (Uses a predefined mixalpha charset).
4. **Pattern-Specific Wordlists**
    
	    Syntax:
        - `@`: Lowercase letters
        - `,`: Uppercase letters
        - `%`: Numbers
        - `^`: Symbols
    - Example 1: `crunch 10 10 -t manav^%%%%` (Generates    passwords with a specific   pattern).
    - Example 2: `crunch 10 10 -f /usr/share/crunch/charset.lst numeric -t %%%%%%%%%% | more` (Generates numeric passwords like phone numbers).
5. **Permutations**
    
    - Generates combinations of words or phrases in all possible orders.
    - Syntax: `crunch <min> <max> -p <word1> <word2> ...`
    - Example: `crunch 4 6 -p amit malhotra june` (Permutates "amit", "malhotra", "june").
6. **Breaking Wordlists into Chunks**
    
    - Allows splitting large wordlists into manageable pieces.
    - **By Lines**: `crunch 4 5 abcde -c 10 -o START` (Creates files with 10 lines each).
    - **By Size**: `crunch 4 4 -t %%%% -b 1kb -o START` (Creates files of 1 KB each).
7. **Handling Frequency of Characters**
    
    - Controls repetition of characters.
    - Syntax: `crunch <length> <length> <characters> -d <frequency><type>`
        - `@`: Lowercase
        - `,`: Uppercase
        - `%`: Numbers
    - Example: `crunch 9 9 sumitpa -d 2@ | more` (Limits repetition of lowercase characters to 2).
8. **Inversion of Output**
    
    - Reverses the order of generated passwords.
    - Example: `crunch 8 8 -t Pass@%%% -l aaaa@aaa -i | more`.

---
## **Installation**

- Command: `apt-get install crunch`

---

## **Common Use Cases**

1. **User-Specific Wordlists**
    - Design based on the target's habits or known data.
2. **Pattern-Based Passwords**
    - E.g., Passwords containing a specific symbol or format.
3. **Handling Large Files**
    - Break down large wordlists for easier transportation or analysis.

---
