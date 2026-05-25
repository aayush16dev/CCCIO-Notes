
# **Practical: Combining Three Wordlists Using dymerge on Kali Linux**

## Key Points

* **dymerge** is a Python-based tool used for merging and cleaning wordlists efficiently.

* It removes duplicate entries and can sort the final output automatically.

* The wordlists used in this practical are:

  * `xzy.txt`

  * `rbg.txt`

  * `abc.txt`

---

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Python Installed**: Required to run the dymerge script.

3. **Internet Connectivity**: Required to download the tool from GitHub.

4. **Terminal Access**: Needed to execute commands.

5. **Sample Wordlists**: `xzy.txt`, `rbg.txt`, and `abc.txt`.

---

# Commands as Steps

## 1. Clone the dymerge Repository

```bash id="x4m8vp"
git clone https://github.com/k4m4/dymerge.git

cd dymerge
```

### Explanation

Downloads the dymerge project from GitHub and navigates into the project directory.

---

## 2. Make the Script Executable

```bash id="p7u2kd"
chmod +x dymerge.py
```

### Explanation

Grants execute permissions to the `dymerge.py` script.

---

## 3. Merge the Wordlists

```bash id="r3n6qy"
./dymerge.py /home/monarch/Desktop/wrdlst -u -f -o superwrdlst.txt
```

### Explanation

Merges multiple wordlists stored in the specified directory and saves the output into a new file.

* `-o superwrdlst.txt` specifies the output filename.

* `-u` removes duplicate entries from the merged list.

* `-f` forces the merge operation.

---

# Explanation of Additional Options

| Option             | Usage                             |
| ------------------ | --------------------------------- |
| `-o %3Coutput_file%3E` | Defines the output file name      |
| `-d <delimiter>`   | Sets a custom delimiter           |
| `-i`               | Ignores case sensitivity          |
| `-u`               | Removes duplicate entries         |
| `-s`               | Sorts the wordlist alphabetically |
| `-h`               | Displays the help menu            |
| `--version`        | Displays the dymerge version      |

---

## 4. Verify the Merged Wordlist

```bash id="k9w5tm"
cat superwrdlst.txt
```

### Explanation

Displays the contents of the merged output file containing unique words from all wordlists.

---

