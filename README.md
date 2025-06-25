# Mass WordPress Installer & Setup Tool
This is a powerful and concurrent Go-based tool designed to automate the process of installing and setting up WordPress on a massive scale. It intelligently scans a list of websites, detects vulnerable installation pages (install.php) and database setup pages (setup-config.php), and attempts to perform an automated installation using credentials you provide.

The tool is built for efficiency, utilizing Goroutines for high-speed, parallel processing, and provides clear, color-coded feedback directly in your console.

# ✨ Key Features
⚡ High-Speed & Concurrent: Utilizes Go's concurrency model with configurable workers to scan and process hundreds or thousands of sites in a very short amount of time.

🧠 Smart Detection: Automatically follows redirects to find the correct install.php or setup-config.php pages, maximizing the chances of a successful installation.

🤖 Fully Automated Installation:

Completes the standard 2-step WordPress installation process.

Automatically configures the database (wp-config.php) if a setup-config.php page is found.

✅ Clean & Organized Reporting:

installed-wp.txt: A clean list of successfully installed sites with their corresponding credentials.

trymanually.txt: A dedicated list for sites where an installation page was found but the automated process failed, preventing duplicate checks and saving time.

⚙️ Flexible Modes:

Interactive Mode: A user-friendly prompt for beginners to provide file paths and settings.

Command-Line Mode: Directly pass arguments for easy integration into automated workflows.

🚀 First-Time Setup: If no .env file is found, the script initiates an interactive setup to securely create one for your credentials, making it easy to get started.

🎨 Rich Console Output: Enjoy a colorful, well-structured, and informative console output that makes it easy to track the tool's progress.

# 🛠️ Usage
This guide covers how to run the pre-built executable on both Linux and Windows.

1. Configuration
The tool uses a .env file to store your credentials. Place the executable in a directory. On the first run, the tool will guide you to create a .env file, or you can create it manually in the same directory.

Create a file named .env and fill it with your desired credentials:

# WordPress Installation Credentials
BLOG_TITLE=My New Awesome Blog
USERNAME=admin
PASSWORD=YourSecurePasswordHere
EMAIL=your-email@example.com

# Database Setup Credentials
DB_HOST=localhost
DB_NAME=wordpress_db
DB_USERNAME=wp_user
DB_PASSWORD=YourSecureDbPassword

2. Prepare Your Lists
In the same directory as the executable, create the following files:

A sites.txt file with one domain per line (e.g., example.com).

A paths.txt file with one path per line (e.g., /blog, /wp).

3. Running the Tool
You have two options for running the executable:

A) Interactive Mode (Recommended for ease of use)

Simply run the program without any arguments. It will prompt you for the file paths and the number of workers.

For Linux:

./wp-installer-linux

For Windows (Command Prompt or PowerShell):

.\wp-installer.exe

B) Command-Line Mode (For automation)

Provide the paths to your sites and paths files as arguments.

For Linux:

# Usage: ./wp-installer-linux <sites_file> <paths_file> [worker_count]
./wp-installer-linux sites.txt paths.txt 50

For Windows (Command Prompt or PowerShell):

# Usage: .\wp-installer.exe <sites_file> <paths_file> [worker_count]
.\wp-installer.exe sites.txt paths.txt 50

# 💡 How It Works
The tool takes a list of websites and a list of common paths (e.g., /blog, /wp) as input.

It creates a job queue of all possible site/path combinations.

Multiple concurrent workers pick jobs from the queue.

Each worker checks if the URL redirects to a WordPress installation or setup page.

If a vulnerable page is found:

It first attempts to configure the database if needed (setup-config.php).

It then proceeds to perform the final WordPress installation with the provided user details.

Results are logged to the appropriate output files (installed-wp.txt or trymanually.txt). The internal state ensures no site is ever processed twice.

# ⚠️ Disclaimer
This tool is intended for educational purposes and for penetration testers to use on systems they are authorized to test. The user is responsible for their actions and must obey all applicable laws. The developer assumes no liability and is not responsible for any misuse or damage caused by this program.
