## Secure Coding Review
Step 1: Choosing a Programming Language and Application
Programming Language: Python
Application: An open-source web application written in Python using the Flask framework

Step 2: Identifying an Application for Review
Example : Checkout "Sample flask app code.py"
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

Step 4: Documenting Findings and Provide Recommendations
Generating a security report highlighting identified vulnerabilities and recommendations for secure coding practices.
![Secure coding review](https://github.com/user-attachments/assets/eae0310a-d422-4ad8-acd5-a0abdda3e05f)

Step 5: Implemented Secure Coding Practices
Example : Checkout "Secure code implementation.py"

Applied Fixes:
✅ SQL Injection Prevention:
Parameterized queries (cursor.execute(query, (username, password))) prevent SQL injection attacks.

✅ Input Validation:
Strips unnecessary whitespace and ensures both fields are provided before processing.

✅ Secure Debug Mode Handling:
Disabled debug mode (app.run(debug=False)) to prevent sensitive information leakage.

