
- gathering as much information about the target as possible without making assumptions
- port scanning
- nmap -sV -sC -p- 10.49.181.3
- exploring the application
- curl -I http://10.49.181.3
- directory enumeration
- gobuster dir -u http://10.49.181.3 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -x php -x php
- <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6e09ed25-c319-4a1a-8a79-b2683c5fcde1" />
- This output tells us a great deal. Let's break down the important discoveries:

- /admin - An admin panel exists, but it redirects to the login page. We will need credentials to access it.
- /api - An endpoint is present. APIs often expose data in ways the frontend does not.
- /reset.php - A password reset page. Reset mechanisms are frequently implemented insecurely.
- /uploads - An uploads directory. If we can upload files, this could be a path to code execution.
- /profile.php and /dashboard.php - These require authentication, so we need to be logged in to access them.
