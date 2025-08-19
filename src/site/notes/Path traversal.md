---
{"dg-publish":true,"permalink":"/path-traversal/"}
---

- [GitHub - omurugur/Path\_Travelsal\_Payload\_List: Path Traversal Vulnerability Payload List](https://github.com/omurugur/Path_Travelsal_Payload_List)
- [Linux Path Traversal Cheatsheet](https://gist.github.com/SleepyLctl/63a2da730a3d5abce5013f0f510b1fe2)
- [Path Traversal \| OWASP Foundation](https://owasp.org/www-community/attacks/Path_Traversal)
- [Linux Path Traversal Cheatsheet](https://gist.github.com/SleepyLctl/63a2da730a3d5abce5013f0f510b1fe2)
- [GitHub - JahTheTrueGod/Directory-Traversal-Cheat-Sheet: Directory traversal refresher](https://github.com/JahTheTrueGod/Directory-Traversal-Cheat-Sheet)


## Related [[CVE\|CVE]]s


|             |                                                                         |
| ----------- | ----------------------------------------------------------------------- |
| [[CoreFTP\|CoreFTP]] | [NVD - CVE-2022-22836](https://nvd.nist.gov/vuln/detail/CVE-2022-22836) |


#### Directory Traversal and [[Concept of Attack\|Concept of Attack]]

```bash
curl -k -X PUT -H "Host: <IP>" --basic -u <username>:<password> --data-binary "PoC." --path-as-is https://<IP>/../../../../../../whoops
```

| **Step** | **Directory Traversal**                                                                                                                                                                                                                                      | **Concept of Attacks - Category** |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------- |
| `1.`     | The user specifies the type of [[net/protocols/Hypertext Transfer Protocol\|HTTP]] request with the file's content, including escaping **characters to break out of the restricted area**.                                                                                 | `Source`                          |
| `2.`     | The changed type of HTTP request, file contents, and path entered by the user are taken over and processed by the process.                                                                                                                                   | `Process`                         |
| `3.`     | The application checks whether the user is authorized to be in the specified path. ==Since the restrictions only apply to a specific folder==, all permissions granted to it are **bypassed** as it breaks out of that folder using the directory traversal. | `Privileges`                      |
| `4.`     | The destination is another process that has the task of writing the specified contents of the user on the local system.                                                                                                                                      | `Destination`                     |

#### Arbitrary File Write

| **Step** | **Arbitrary File Write**                                                                                                                            | **Concept of Attacks - Category** |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| `5.`     | The same information that the user entered is used as the source. In this case, the filename (`whoops`) and the contents (`--data-binary "PoC."`).  | `Source`                          |
| `6.`     | The process takes the specified information and proceeds to write the desired content to the specified file.                                        | `Process`                         |
| `7.`     | Since all restrictions were bypassed during the directory traversal vulnerability, the service approves writing the contents to the specified file. | `Privileges`                      |
| `8.`     | The filename specified by the user (`whoops`) with the desired content (`"PoC."`) now serves as the destination on the local system.                | `Destination`                     |

## Examples

```bash
get_file() {  curl -s http://titanic.htb/download?ticket=../../../$1; }
```