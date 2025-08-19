---
{"dg-publish":true,"permalink":"/sre/tools/tmux/"}
---

## Links

- [[Tmux - Mouse Support\|Tmux - Mouse Support]]
- [[Tmux - rename pane\|Tmux - rename pane]]
- [[Tmux - rename session\|Tmux - rename session]]
- [[Tmux Plugin Manager - TPM\|Tmux Plugin Manager - TPM]]
- [[Tmux - go into scroll mode\|Tmux - go into scroll mode]]

---

- [[TMUX Cheatsheet\|TMUX Cheatsheet]]


- https://linuxhint.com/customize-tmux-configuration/
- https://www.linuxtrainingacademy.com/tmux-tutorial/#:~:text=To%20attach%20or%20reattach%20to,are%20all%20the%20same%20command.
## Stackoverflow posts

- Mouse mode: https://superuser.com/questions/210125/scroll-shell-output-with-mouse-in-tmux


## Increase scrollback buffer


See,  [[Tmux Plugin Manager - TPM\|Tmux Plugin Manager - TPM]]
## Reference

1. [Getting started with tmux | ITTavern.com](https://ittavern.com/getting-started-with-tmux/)
2. [tmux - ArchWiki](https://wiki.archlinux.org/title/tmux)
3. [Rename Tmux Windows - Today I Learned](https://til.hashrocket.com/posts/18b63da9d2-rename-tmux-windows)
### Plugins

1. [GitHub - christoomey/vim-tmux-navigator: Seamless navigation between tmux panes and vim splits](https://github.com/christoomey/vim-tmux-navigator#restoring-clear-screen-key-binding)
2. [tmuxifier/README.md at master · jimeh/tmuxifier · GitHub](https://github.com/jimeh/tmuxifier/blob/master/README.md)


# Tmux create or attach

```bash
tmux new-session -A -s main
```