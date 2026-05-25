# **Hosting a Website Locally on Kali Linux Using a Single Command**

## Objective
The objective of this practical is to demonstrate how to host a website locally on Kali Linux using a single command. This method is useful for quickly serving web content during development or testing.

## Pre-requisites
1. **Kali Linux**: Ensure you have Kali Linux installed and running.
2. **Python**: Ensure Python is installed on your system, as the command uses Python's built-in HTTP server.

## Commands as Steps

1. **Navigate to the Directory Containing Your Website Files**
   ```bash
   cd /path/to/your/website
   ```
   **Explanation**: Replace `/path/to/your/website` with the actual path to the directory containing your website files. This could be an HTML file, a set of static files, or a directory structure for your website.

2. **Start the Local HTTP Server**
   ```bash
   python -m http.server
   ```
   **Explanation**: This command starts a simple HTTP server using Python's built-in HTTP server module. By default, it serves files from the current directory and listens on port 8000.

## Example Usage

### Hosting a Simple HTML Website

1. **Create a Simple HTML File**
   ```bash
   echo "<html><body><h1>Hello, World!</h1></body></html>" > index.html
   ```
   **Explanation**: This command creates a simple HTML file named `index.html` with the content "Hello, World!".

2. **Navigate to the Directory Containing the HTML File**
   ```bash
   cd /path/to/your/website
   ```
   **Explanation**: Replace `/path/to/your/website` with the actual path to the directory containing the `index.html` file.

3. **Start the Local HTTP Server**
   ```bash
   python -m http.server
   ```
   **Explanation**: This command starts the local HTTP server. You should see output indicating that the server is running and listening on port 8000.

4. **Access the Website in Your Browser**
   Open your web browser and navigate to `http://localhost:8000` to access the locally hosted website. You should see the "Hello, World!" message displayed.

### Hosting a Directory of Static Files

1. **Create a Directory Structure for Your Website**
   ```bash
   mkdir -p /path/to/your/website/{css,js,images}
   ```
   **Explanation**: This command creates a directory structure with subdirectories for CSS, JavaScript, and images.

2. **Add Some Static Files**
   ```bash
   echo "<html><body><h1>Welcome to My Website</h1></body></html>" > /path/to/your/website/index.html
   echo "body { background-color: lightblue; }" > /path/to/your/website/css/style.css
   echo "console.log('Hello, World!');" > /path/to/your/website/js/script.js
   ```
   **Explanation**: These commands create some example static files in the directory structure.

3. **Navigate to the Directory Containing Your Website Files**
   ```bash
   cd /path/to/your/website
   ```
   **Explanation**: Replace `/path/to/your/website` with the actual path to the directory containing your website files.

4. **Start the Local HTTP Server**
   ```bash
   python -m http.server
   ```
   **Explanation**: This command starts the local HTTP server. You should see output indicating that the server is running and listening on port 8000.

5. **Access the Website in Your Browser**
   Open your web browser and navigate to `http://localhost:8000` to access the locally hosted website. You should see the "Welcome to My Website" message displayed, and the CSS and JavaScript files should be served correctly.

