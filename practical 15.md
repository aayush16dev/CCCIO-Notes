---

# **CUPP – Common User Password Profiler**

---

---
# **Bulk Extractor**

---
## **Overview**

**Bulk Extractor** is a powerful forensic analysis tool in Kali Linux used to extract valuable information from disk images, files, or directories.  
It scans raw data and extracts features **without depending on the file system structure**.

---
## **Key Features & Capabilities**

### **Feature Extraction**

Bulk Extractor can identify and extract:

- Email addresses
- URLs
- Credit card numbers 
- Phone numbers
- File names
- Passwords
- Network information
- Document metadata

### **Supported Data Sources**

Bulk Extractor can analyze:

- Disk images
- Individual files
- Directories of files

### **Performance**

- Designed for **high speed**
- Can process **large data sets efficiently**

### **Output Format**

- Extracted information is stored in **feature files**
- Output files are easy to inspect and process with other forensic tools

---

## **Basic Usage**

### **1. Open Terminal**

Press:

```
Ctrl + Alt + T
```

### **2. Navigate to Target Directory**

```
cd /path/to/your/file
```

### **3. Run Bulk Extractor**

```
bulk_extractor -o output_directory your_file.ext
```

- `output_directory` → folder where results will be saved
    
- `your_file.ext` → file or disk image to analyze
    

### **4. View Results**

After completion, all extracted features will appear inside the specified output directory.

---

## **Example 1**

Extract data from a disk image named `disk.img`:

```
bulk_extractor -o extracted_data disk.img
```

---

## **Common Additional Options**

|Option|Purpose|
|---|---|
|`-e email`|Extract only email addresses|
|`-C`|Set context window size|
|`-d`|Enable debug mode|

Example:

```
bulk_extractor -e email -o output disk.img
```

---

## **Example 2: Using Bulk Extractor with a Pendrive**

### **Step 1: Identify Pendrive**

```
lsblk
```

Look for your USB device (e.g., `/dev/sdb`).

### **Step 2: Run Bulk Extractor**

```
sudo bulk_extractor -o output_directory /dev/sdb
```

### **Explanation**

- `sudo` → required for raw device access
    
- `bulk_extractor` → tool name
    
- `-o output_directory` → output folder
    
- `/dev/sdb` → pendrive device path
    

---

## **Key Points**

- Works directly on **raw data**, not file system
    
- Extremely useful in **digital forensics & incident response**
    
- Capable of extracting hidden artifacts from damaged or deleted data
    
- Output integrates easily with other forensic analysis tools
    

---
