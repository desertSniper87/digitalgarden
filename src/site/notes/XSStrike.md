---
{"dg-publish":true,"permalink":"/xs-strike/"}
---

- [GitHub - s0md3v/XSStrike: Most advanced XSS scanner.](https://github.com/s0md3v/XSStrike)

```shell-session
git clone https://github.com/s0md3v/XSStrike.git
cd XSStrike
pip install --break-system-packages -r requirements.txt
```


```bash
python xsstrike.py -u http://94.237.49.226:45061?fullname=a&username=b&password=c&email=dees@essw.fc
```
