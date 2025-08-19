---
{"dg-publish":true,"permalink":"/dom-based-xss/"}
---


- The third and final type of [[net/sec/Cross Side Scripting\|XSS]] is another Non-Persistent type called DOM-based XSS.
- DOM XSS is completely processed on the client-side through JavaScript
- DOM XSS occurs when JavaScript is used to change the page source through the [[Document Object Model\|Document Object Model]] (DOM).
- `innerHTML` function does not allow the use of the `<script>` tags within it as a security feature.

