
---
# **Password Protecting a Text File in Windows**

## Objective

The objective of this practical is to learn how to create and access a **password-protected text file** in Windows using the command prompt in order to secure sensitive information from unauthorized access.

## Pre-requisites

1. **Windows Operating System**: A working Windows system.
    
2. **Command Prompt Access**: Required to execute file creation commands.
    
3. **Basic File Handling Knowledge**: Understanding of text files and saving content.
    

## Commands as Steps

1. **Open Command Prompt**
    
    **Action**: Open the Command Prompt (CMD) in Windows.
    
    **Explanation**: The command prompt is required to create and access the protected file.
    
2. **Create a Password-Protected Text File**
    
    ```bash
    notepad filename.txt:password
    ```
    
    **Example**:
    
    ```bash
    notepad amit.txt:123456789
    ```
    
    **Explanation**:  
    Creates a password-protected version of the text file using the specified password.
    
3. **Edit and Save the File**
    
    **Action**:
    
    - Click **Yes** when prompted to create the file.
        
    - Write content into the file and save it.
        
    
    **Explanation**: Stores secure data inside the protected file.
    
4. **Verify the Protected File**
    
    ```bash
    notepad filename.txt:password
    ```
    
    **Explanation**: Opens the password-protected version of the file.
    
    To open the normal version:
    
    ```bash
    notepad filename.txt
    ```
    
    **Explanation**: Accesses the non-protected version of the same file.
    
5. **Store Different Content**
    
    **Action**: Save different data in the protected and non-protected versions of the file.
    
    **Explanation**: Ensures separation of secure and non-secure information.
    

---
