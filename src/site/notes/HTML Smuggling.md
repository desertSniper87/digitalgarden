---
{"dg-publish":true,"permalink":"/html-smuggling/"}
---


# Bypassing an IDS/Firewall through HTML Smuggling

**HTML smuggling** is a type of web attack in which an attacker injects malicious code into an HTML script to compromise a web page.
- This attack allows attackers to manipulate the features of scripting codes (HTML5, JavaScript, etc.) and stay hidden from SIEM solutions, firewalls, web proxies, and email gateways.
- The purpose of HTML smuggling is to successfully install the malware payload on a target system when the victim accesses the malicious link sent via phishing email.

An attacker creates a malicious link by developing a JavaScript-based blob with a compatible MIME that is set to automatically download the malware.
- The attacker can use tools such as **HTML Smuggler** to develop a JS payload for firewall/IDS bypass and deliver it via an HTML attachment.
- Once the malware is executed, it provides remote access to the attacker to launch persistent attacks.

## Working of HTML Smuggling

1. Attackers initiate an attack by embedding malware within a HTML5 attachment or web page. When the victim clicks on the malicious link, the specially crafted malware executes on the victim system.
```html
<a href="malicious.doc" download="Myfile.doc">Click</a>
```
1. The executed malware is saved with an unsuspicious name on the device.
2. Attackers can also perform HTML smuggling using JavaScript, as shown below:
```js
var myAnchorElement = myAnchorElement.download = 'Myfile.doc'; 
document.createElement('a');
```
4. In this case, the malicious file is built using the JavaScript **Blob**. Instead of supplying a URL for the malicious file to be downloaded, the file itself can be built from the Blob:
```js
var fakeBlob = new Blob([myfakeFile], {type: 'octet/stream'});
```
5. Attackers create a URL to lure victims into downloading the malicious file:
```js
var myfileUrl = myAnchor.href = myfileUrl; 
myAnchor.click();
```

  

  

The IDS/firewall expects JavaScript and HTML traffic from the clients. The JavaScript actually hides the blob content to evade detection and allows a connection with the malicious server.

  

## **Signs of HTML Smuggling**

  

Signs of malware-smuggling HTML attachments include:

- A ZIP file with JavaScript
- An encrypted attachment
- Existence of suspicious script code within an HTML-based file
- Decoding of HTML-based file using Base64
    

  

## **Countermeasures**

- Block auto-execution of .js and .jse files.
    
- Ensure Office 365 email security filtering is actively barring auto-download of malware-loaded mails.
    
- Verify the perimeter operation of security devices such as firewall and proxy restricting arbitrary server connections to the Internet.
    
- Recommend users to access web browsers activated with **Microsoft Defender SmartScreen** and network protection to avert and block malicious access.
    
- Enable cloud delivery-based protection using AI and ML technology for identification and prevention of threats.
    
- Implement **CSP** headers on the web server.
    
- Define a whitelist of allowed HTML tags, attributes, and protocols.
    
- Encode all dynamic content before rendering it in the browser.
    

```
window.URL.createObjectURL(fakeBlob);
```
