---
{"dg-publish":true,"permalink":"/apple/tools/installation-of-cocoapods/"}
---


## Prerequisites

1. Xcode developement tools
2. Ruby >=2.7.0 (**Please make sure you have >=3.2.0 as most projects will fail**)
3. [[apple/Tools/Homebrew\|Homebrew]]


```bash
sudo gem install cocoapods
```

### Alternative

***Do no do this for older projects. It will install cocoapod ~1.5 whereas `gem install cocoapods` will install 1.1 [More info](https://stackoverflow.com/a/74154822/7154462)***

- https://stackoverflow.com/a/52990197/7154462

```bash
brew install --cask cocoapods
```

## Errors

### You need to install development tools first

```bash
xcode-select --install
```

## Ruby Installation

!
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



### Installation of Ruby ~~2.6.3~~ 3.2.2
```bash
brew install rbenv ruby-build
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile 
rbenv install 3.2.2
rbenv global 3.2.2
```


</div></div>


#### References

1. [vim - macOS Mojave 'ruby/config.h' file not found - Stack Overflow](https://stackoverflow.com/questions/53135863/macos-mojave-ruby-config-h-file-not-found)