# Cookies and Sessions

## What I learned today
- Cookies store small pieces of data in the browser.
- Sessions store user data on the server.
- Cookies identify you sessions store your information.
- Cookies + sessions = how websites keep you logged in.
- If someone steals your cookie, they can become you (session hijacking).

## Cookies (Browser Storage)
- Small text data saved in your browser.
- Automatically sent with every request.
- Used for:
  - Login state
  - Preferences
  - Shopping carts
  - Tracking

### Example:
session_id=abc123xyz

## Sessions (Server Storage)
- Data stored on the server about the user.
- Linked to the user by the session ID in the cookie.
- Stores:
  - Username
  - Login status
  - Permissions
  - Cart items

## How Cookies and Sessions Work Together
1. User logs in.
2. Server creates a session.
3. Server sends a cookie with session ID.
4. Browser stores the cookie.
5. Browser sends the cookie on every request.
6. Server checks the session ID and knows who you are.

## Types of Cookies
- Session cookies → deleted when browser closes  
- Persistent cookies → stay on device  
- Secure cookies → only sent over HTTPS  
- HttpOnly cookies → cannot be accessed by JavaScript  
- SameSite cookies → protect against CSRF  

## Why This Matters in Cybersecurity
- Attackers steal cookies to hijack accounts.
- HTTPS protects cookies from being sniffed.
- HttpOnly protects against XSS.
- SameSite protects against CSRF.



## Questions
- What is a packet?
