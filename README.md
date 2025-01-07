## Secure Coding Review
Step 1: Choosing a Programming Language and Application
Programming Language: Python
Application: An open-source web application written in Python using the Flask framework

Step 2: Identifying an Application for Review (Sample flask app code.py)
Analyzing an open-source Flask web application. Flask is a lightweight web framework used for building APIs and web applications.

Step 3: Reviewing the Code for Security Vulnerabilities
Identified Security Issues:
1. SQL Injection :
- The query in the /login route uses string formatting (f"SELECT * FROM users WHERE username = '{username}' AND password = '{password}'"), making it vulnerable to SQL injection.
- An attacker can bypass authentication using ' OR '1'='1 as the username.

2. Hardcoded Credentials Risk
- The database query directly includes user input without any validation.

3. Lack of Input Validation
- The application does not validate username or password before using them in SQL queries.

4. Debug Mode Enabled
- Running Flask in debug=True mode can expose sensitive information and allow arbitrary code execution.

Step 4: Document Findings and Provide Recommendations
Generating a security report highlighting identified vulnerabilities and recommendations for secure coding practices.
