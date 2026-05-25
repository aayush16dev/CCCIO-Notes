# **Using Steghide on Kali Linux for Steganography**

## Objective
The objective of this practical is to use Steghide on Kali Linux to hide and extract secret messages within image files. Steganography is the practice of hiding secret information within non-secret data, such as images, audio, or video files.

## Pre-requisites
1. **Kali Linux**: Ensure you have Kali Linux installed and running.
2. **Steghide**: Ensure Steghide is installed on your system. Steghide is a steganography tool that can hide data within image and audio files.

## Commands as Steps

1. **Install Steghide**
   ```bash
   apt install steghide
   ```
   **Explanation**: This command installs Steghide, a tool used for hiding and extracting secret messages within image and audio files.

2. **Create a Secret Message File**
   ```bash
   echo "This is a secret message" > secret.txt
   ```
   **Explanation**: This command creates a file named `secret.txt` containing the secret message "This is a secret message".

3. **Embed the Secret Message in an Image**
   ```bash
   steghide embed -cf image.jpg -ef secret.txt
   ```
   **Explanation**: This command embeds the secret message (`secret.txt`) into the image file (`image.jpg`). The `-cf` option specifies the cover file (the image file), and the `-ef` option specifies the embedded file (the secret message file).

4. **Set a Passphrase (Optional but Recommended)**
   ```bash
   steghide embed -cf image.jpg -ef secret.txt
   ```
   **Explanation**: When prompted, enter a passphrase to encrypt the hidden data. This adds an extra layer of security to the hidden message.

5. **Verify the Embedded Data**
   ```bash
   steghide info image.jpg
   ```
   **Explanation**: This command displays information about the embedded data in the image file, including the size of the hidden data and the passphrase (if set).

6. **Extract the Secret Message**
   ```bash
   steghide extract -sf image.jpg
   ```
   **Explanation**: This command extracts the hidden data from the image file. If a passphrase was set during embedding, you will be prompted to enter it.

7. **View the Extracted Secret Message**
   ```bash
   cat secret.txt
   ```
   **Explanation**: This command displays the contents of the extracted secret message file.

## Example Usage

### Hiding a Secret Message in an Image

1. **Create a Secret Message File**
   ```bash
   echo "This is a secret message" > secret.txt
   ```
   **Explanation**: This command creates a file named `secret.txt` containing the secret message "This is a secret message".

2. **Embed the Secret Message in an Image**
   ```bash
   steghide embed -cf image.jpg -ef secret.txt
   ```
   **Explanation**: This command embeds the secret message (`secret.txt`) into the image file (`image.jpg`). When prompted, enter a passphrase to encrypt the hidden data.

3. **Verify the Embedded Data**
   ```bash
   steghide info image.jpg
   ```
   **Explanation**: This command displays information about the embedded data in the image file, including the size of the hidden data and the passphrase (if set).

### Extracting the Secret Message from the Image

1. **Extract the Secret Message**
   ```bash
   steghide extract -sf image.jpg
   ```
   **Explanation**: This command extracts the hidden data from the image file. If a passphrase was set during embedding, you will be prompted to enter it.

2. **View the Extracted Secret Message**
   ```bash
   cat secret.txt
   ```
   **Explanation**: This command displays the contents of the extracted secret message file, which should be "This is a secret message".
