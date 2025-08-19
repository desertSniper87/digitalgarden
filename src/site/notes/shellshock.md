---
{"dg-publish":true,"permalink":"/shellshock/"}
---


```shell-session
$ env y='() { :;}; echo vulnerable-shellshock' bash -c "echo not vulnerable"
```