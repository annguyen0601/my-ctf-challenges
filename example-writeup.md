# Example CTF Challenge

## Description

**Category:** Web  
**Difficulty:** Easy  
**Points:** 100  

You are given a web application that appears to be a simple login form. The challenge description states: "Can you find a way to bypass the authentication?"

The application is hosted at `http://example-ctf.com/login`

## Solution

### Initial Analysis

When visiting the login page, we see a standard username and password form. Let's start by examining the page source.

### Tools Used
- Burp Suite
- Browser Developer Tools

### Step-by-Step Approach

1. **Examined the HTML source code**: Found a JavaScript file `auth.js` that handles the login validation
2. **Analyzed the JavaScript**: The authentication logic was implemented client-side
3. **Discovered the vulnerability**: The password check was done using a simple comparison in JavaScript:
   ```javascript
   if (password === "sup3r_s3cr3t_p4ss") {
       return true;
   }
   ```
4. **Exploited the vulnerability**: Used the discovered password to login
5. **Retrieved the flag**: After successful login, the flag was displayed on the dashboard

### Key Insights

This challenge demonstrates why authentication should never be performed on the client-side. Always implement authentication on the server-side where the logic cannot be easily inspected or bypassed.

### Flag
```
flag{client_side_auth_is_bad}
```
