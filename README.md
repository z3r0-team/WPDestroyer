
# Mass WordPress Installer & Setup Tool

This is a powerful and concurrent Go-based tool designed to automate the process of installing and setting up WordPress on a massive scale. It intelligently scans a list of websites, detects vulnerable installation pages (install.php) and database setup pages (setup-config.php), and attempts to perform an automated installation using credentials you provide.

The tool is built for efficiency, utilizing Goroutines for high-speed, parallel processing, and provides clear, color-coded feedback directly in your console.


## Features

- ⚡ High-Speed & Concurrent: Utilizes Go's concurrency model with configurable workers to scan and process hundreds or thousands of sites in a very short amount of time.

- 🧠 Smart Detection: Automatically follows redirects to find the correct install.php or setup-config.php pages, maximizing the chances of a successful installation.

- 🤖 Fully Automated Installation: Completes the standard 2-step WordPress installation process. Automatically configures the database (wp-config.php) if a setup-config.php page is found.

- Interactive Mode: A user-friendly prompt for beginners to provide file paths and settings.

- Command-Line Mode: Directly pass arguments for easy integration into automated workflows.

- 🚀 First-Time Setup: If no .env file is found, the script initiates an interactive setup to securely create one for your credentials, making it easy to get started


## Usage/Examples
For Linux :

```
./destroy
./destroy <sites_file> <paths_file> [worker_count]
```
For Windows :
```
destroy.exe
destroy.exe <sites_file> <paths_file> [worker_count]
```

## Example for <sites_file>
```
google.com
facebook.com
github.com
```
## Example for <paths_file>
```
/wp/
/wordpress/
/staging/
```
## Screenshots

![App Screenshot](https://l.top4top.io/p_3462ondes1.jpg)


## Authors

- [@z3r0-team](https://github.com/z3r0-team)
- Indonesian People
- #CianjurHacktivist!

