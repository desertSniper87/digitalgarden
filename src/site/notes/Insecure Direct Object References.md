---
{"dg-publish":true,"permalink":"/insecure-direct-object-references/"}
---

- [WSTG - Latest \| OWASP Foundation](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/05-Authorization_Testing/04-Testing_for_Insecure_Direct_Object_References)


- What makes this attack very common is essentially the lack of a solid access control system on the back-end
- As web applications store users' files and information
- they may use sequential numbers or user IDs to identify each item
- Suppose the web application lacks a robust access control mechanism and exposes direct references to files and resources
- We may access other users' files and information by simply guessing or calculating their file IDs.


## IDOR Mitigation

- Ensure Object-Level Access Control

```javascript
match /api/profile/{userId} {
    allow read, write: if user.isAuth == true
    && (user.uid == userId || user.roles == 'admin');
}
```


- Implement