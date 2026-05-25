
---
# **Creating Colored Text Art on Terminal in Kali Linux**

## Objective

The objective of this practical is to learn how to create colorful ASCII text art on the Kali Linux terminal using **figlet** and **lolcat**, and to configure the terminal to display custom text art automatically at startup.

## Pre-requisites

1. **Kali Linux System**: A running Kali Linux installation.
    
2. **Internet Connection**: Required to download tools and fonts.
    
3. **Terminal Access**: Needed to execute installation and configuration commands.
    
4. **Basic Linux Knowledge**: Familiarity with file editing and terminal usage.
    

## Commands as Steps

1. **Install Required Tools**
    
    ```bash
    apt-get install figlet
    apt-get install lolcat
    ```
    
    **Explanation**: Installs **figlet** for ASCII text generation and **lolcat** for colorful terminal output.
    
2. **Generate Basic Text Art**
    
    ```bash
    figlet <text>
    ```
    
    **Example**:
    
    ```bash
    figlet Massmatic
    ```
    
    **Explanation**: Creates simple ASCII text art from the given input text.
    
3. **Generate Colored Text Art**
    
    ```bash
    figlet <text> | lolcat
    ```
    
    **Example**:
    
    ```bash
    figlet Massmatic | lolcat
    ```
    
    **Explanation**: Pipes the figlet output through lolcat to add colorful effects.
    
4. **Center the Text**
    
    ```bash
    figlet -c <text>
    ```
    
    **Example**:
    
    ```bash
    figlet -c Amit
    ```
    
    **Explanation**: Displays the generated text in the center of the terminal.
    
5. **Download Additional Fonts**
    
    ```bash
    git clone https://github.com/xero/figlet-fonts.git
    cd figlet-fonts
    mv * /usr/share/figlet
    ```
    
    **Explanation**: Downloads extra figlet fonts and installs them for extended design options.
    
6. **Apply Custom Fonts**
    
    ```bash
    figlet -f "<font-name>" -c <text>
    ```
    
    **Example**:
    
    ```bash
    figlet -f "ANSI Regular.flf" -c Amit
    ```
    
    Add colors:
    
    ```bash
    figlet -f "ANSI Regular.flf" -c Amit | lolcat
    ```
    
    **Explanation**: Uses a selected font and applies color effects.
    
7. **Configure Startup Text Art**
    
    ```bash
    mousepad .zshrc
    ```
    
    Add the following lines at the end of the file:
    
    ```bash
    clear
    figlet -f "ANSI Regular.flf" -c Massmatic | lolcat
    figlet -f digital.flf -c "Dive Into Cyber World" | lolcat
    ```
    
    **Explanation**: Automatically displays custom colored text whenever the terminal opens.
    
8. **Save and Test**
    
    **Action**: Save the file, close the editor, and reopen the terminal.
    
    **Explanation**: Confirms that the text art appears on terminal startup.
    

---](<---

# **Creating Colored Text Art on Terminal in Kali Linux**

## Objective

The objective of this practical is to learn how to create colorful ASCII text art on the Kali Linux terminal using **figlet** and **lolcat**, and to configure the terminal to display custom text art automatically at startup.

---

## Pre-requisites

1. **Kali Linux System**: A running Kali Linux installation.

2. **Internet Connection**: Required to download tools and fonts.

3. **Terminal Access**: Needed to execute installation and configuration commands.

4. **Basic Linux Knowledge**: Familiarity with terminal commands and file editing.

---

# Commands as Steps

## 1. Install Required Tools

```bash id="9y8f6k"
apt-get install figlet

apt-get install lolcat
```

### Explanation

* `figlet` is used to generate ASCII text art.

* `lolcat` adds colorful rainbow effects to terminal output.

---

## 2. Generate Basic Text Art

```bash id="9z3c9v"
figlet %3Ctext%3E
```

### Example

```bash id="xj7m2n"
figlet Massmatic
```

### Explanation

Creates ASCII text art using the provided text.

---

## 3. Generate Colored Text Art

```bash id="1f7k2a"
figlet <text> | lolcat
```

### Example

```bash id="4d0mwh"
figlet Massmatic | lolcat
```

### Explanation

Pipes the output of `figlet` into `lolcat` to display colorful text art.

---

## 4. Center the Text

```bash id="v2ndjr"
figlet -c <text>
```

### Example

```bash id="yybrk7"
figlet -c Amit
```

### Explanation

The `-c` option centers the generated text in the terminal window.

---

## 5. Download Additional Fonts

```bash id="mow9nf"
git clone https://github.com/xero/figlet-fonts.git

cd figlet-fonts

mv * /usr/share/figlet
```

### Explanation

* Downloads additional figlet fonts from GitHub.

* Moves the downloaded fonts into the system figlet font directory for use.

---

## 6. Apply Custom Fonts

```bash id="xwn6pq"
figlet -f "<font-name>" -c <text>
```

### Example

```bash id="b7upqv"
figlet -f "ANSI Regular.flf" -c Amit
```

### Add Color Effects

```bash id="1ut6lb"
figlet -f "ANSI Regular.flf" -c Amit | lolcat
```

### Explanation

* `-f` specifies the font style.

* `-c` centers the text.

* `lolcat` adds colorful terminal effects.

---

## 7. Configure Startup Text Art

```bash id="byd0jv"
mousepad .zshrc
```

Add the following lines at the end of the file:

```bash id="y93tye"
clear
figlet -f "ANSI Regular.flf" -c Massmatic | lolcat
figlet -f digital.flf -c "Dive Into Cyber World" | lolcat
```

### Explanation

These commands automatically display customized colored ASCII art whenever a new terminal session starts.

---

## 8. Save and Test

### Action

Save the `.zshrc` file, close the editor, and reopen the terminal.

### Explanation

Verifies that the configured startup text art appears automatically when the terminal launches.

---
