---
{"dg-publish":true,"permalink":"/apple/tools/installation-of-cocoapods/","dgPassFrontmatter":true}
---


## Prerequisites

1. Xcode developement tools
2. Ruby >=2.7.0
3. [[apple/Tools/Homebrew\|Homebrew]]


```bash
sudo gem install cocoapods
```

## Errors

### You need to install development tools first

```bash
xcode-select --install
```

### Installation of Ruby 2.6.3

```bash
brew install rbenv ruby-build
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile 
rbenv install 2.6.3
rbenv global 2.6.3
```


#### References

1. [vim - macOS Mojave 'ruby/config.h' file not found - Stack Overflow](https://stackoverflow.com/questions/53135863/macos-mojave-ruby-config-h-file-not-found)