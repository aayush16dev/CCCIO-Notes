
---

# Practical Guide for Hosting a Local DeepSeek Reasoning Model Using Ollama on Kali Linux

Large Language Models (LLMs) can now be executed locally on personal systems without requiring cloud-based services. This practical demonstrates how to install Ollama on Kali Linux and run the DeepSeek-R1 model locally for reasoning and logic-based tasks.

## Objective:

To install Ollama on Kali Linux and host a local DeepSeek reasoning model for offline AI inference and experimentation.

---

## Prerequisites:

* Kali Linux or any Debian-based Linux distribution
* Internet connectivity
* Minimum 8 GB RAM recommended
* Terminal access with sudo privileges
* Basic understanding of Linux commands

---

# Introduction to Ollama

Ollama is a lightweight framework used to download, manage, and run Large Language Models locally on a computer.

### Features of Ollama

* Run AI models locally
* Offline inference support
* Fast model deployment
* GPU and CPU support
* Simple command-line interface
* Supports multiple open-source LLMs

---

# About DeepSeek-R1

DeepSeek-R1 is a reasoning-oriented AI model designed for:

* Logical problem solving
* Mathematical reasoning
* Coding assistance
* Step-by-step analysis
* Natural language understanding

The `1.5b` version is a lightweight model suitable for systems with limited hardware resources.

---

## Step 1: Install Ollama

Visit the official Ollama website and go to downloads:

[Ollama Official Website](https://ollama.com/)

Run the Linux installation command:

```bash id="w3tq5o"
curl -fsSL https://ollama.com/install.sh | sh
```

**Explanation:**
This command downloads and installs Ollama automatically on the system.

---

## Step 2: Verify Installation

Check whether Ollama is installed correctly:

**Bash**

```bash id="eqtb2o"
ollama --version
```

**Explanation:**
Displays the installed version of Ollama.

---

## Step 3: Run the DeepSeek Model

Choose the desired AI model and execute:

**Bash**

```bash id="ltxfzi"
ollama run deepseek-r1:1.5b
```

**Explanation:**
This command:

1. Downloads the DeepSeek-R1 1.5B model
2. Installs the required model files
3. Starts the local AI inference engine

---

## Step 4: Wait for Model Download

During first execution:

* Ollama downloads the model weights
* Setup may take several minutes depending on internet speed

Example process:

```text id="y7jlwm"
pulling manifest
downloading model layers
verifying sha256 digest
success
```

---

## Step 5: Start Interacting with the Model

After setup completes, a local AI chat interface appears inside the terminal.

Example:

```text id="cq6d1q"
>>> Explain what is cybersecurity
```

Model response:

```text id="jlwm1p"
Cybersecurity is the practice of protecting systems,
networks, and data from unauthorized access and attacks.
```

---

## Functionality of the Local Model

The model performs inference directly on your PC without cloud processing.

### Capabilities

* Reasoning tasks
* Logic-based analysis
* Code generation
* Mathematics solving
* Text summarization
* Question answering

---

## Advantages of Running AI Models Locally

### Privacy
Data remains on the local system.
### Offline Usage
No internet required after download.
### Faster Access
No dependency on external APIs.
### Customization
Multiple models can be downloaded and tested.

---

# Example Use Cases

* Cybersecurity research
* AI experimentation
* Local coding assistant
* Educational purposes
* Offline chatbot systems
* Research and development

---

# Common Ollama Commands

## View Installed Models

**Bash**

```bash id="x3j0nn"
ollama list
```

---

## Remove a Model

**Bash**

```bash id="b0rnyc"
ollama rm deepseek-r1:1.5b
```

---

## Run Another Model

Example:

**Bash**

```bash id="0w2o2g"
ollama run llama3
```

---

# System Requirements

| Component | Recommended              |
| --------- | ------------------------ |
| RAM       | 8 GB or higher           |
| CPU       | Multi-core processor     |
| Storage   | 5 GB+ free space         |
| GPU       | Optional but recommended |

---
