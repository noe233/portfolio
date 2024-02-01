---
title: Navigating Jekyll and Ruby Compatibility on Mac(M1)
tags: [Jekyll, Ruby, chruby, gems]
style: fill
color: info
comments: true
description: Run Jekyll theme locally in macOS.
---


## Introduction

In this blog post, I will document the challenges I faced when attempting to run my Jekyll theme GitHub page website locally on Mac and also how I solved these installing Ruby gems errors.

## The Challenge: Installing gems doesn’t work with the system Ruby

Ruby is preinstalled on Mac and the version is 2.6.10. Jekyll require at least Ruby version 2.7.0, and the preinstalled Ruby version can’t be updated. Additinaly, the system Ruby is missing some libraries. Check with Ruby version you have installed in your system:
```bash
ruby -v
```


## The Decision: Reinstalling Ruby using chruby
To address the compatibility issues, I have to reinstall Ruby and opted for chruby, a versatile Ruby version manager. However, the path to resolving the issue wasn't straightforward, as I had to bid farewell to RVM since only one Ruby version control system is allowed at a time.

## Uninstalling RVM: Clearing the Path for chruby
Before installing chruby, I needed to remove RVM from my system. This involved cleaning up configurations and ensuring a fresh start for the new Ruby version manager.
```bash
# Check if you have other ruby managers
rvm help
# Commands to uninstall RVM
rvm implode
```

```bash
vim ~/.bashrc
```
After running above command to uninstall RVM, we have to make sure to delete references to RVM scripts in the shell configuration file, but the corresponding RVM installation directory or scripts are no longer present on your system. In shell config file, comment out lines relate to RVM.
{% include elements/figure.html image="assets/removervm.png" caption="Commet out both lines" %}
## Installing chruby: Navigating Different Ruby Versions

With RVM out of the picture, it was time to install chruby. This tool would allow me to seamlessly navigate through different Ruby versions, an essential requirement for resolving compatibility issues with Jekyll and its dependencies. Since I already have homebrew installed, I will use it to install chruby.
```bash
# Commands to install chruby
brew install chruby ruby-install
```
## Reinstalling Ruby, Gems, and Bundler

Having set up chruby, the next step was to reinstall Ruby and then proceed to reinstall all required gems and the Bundler. The latest Ruby version is 3.3.0
```bash
#Then install the latest Ruby
ruby-install --latest ruby
```
After install the latest Ruby, we have to check if the latest version is in use.If not, use the following command to chose the new version
```bash
chruby 3.3.0
```
Make sure the new Ruby is in use and now we need to install the bundler.
```bash
gem install bundler
bundle install
```
Here I have encounter a compatibility issue with my ruby version and get this error:Gem::Ext::BuildError: ERROR: Failed to build gem native extension. Therefore I decided to install a diffrent version of ruby(3.0.5)  and it solved the issue.
```bash
#Install another ruby version
ruby-install 3.0.5
#chose the new installed version
chruby 3.0.5
#reinstall bundle
bundle install
#navigate to your jekyll site path and run the command to start your site
bundle exec jekyll serve
```

## An Alternative Solution: Docker Image

For those seeking an alternative, a Docker image can provide an isolated and reproducible environment for Jekyll development. While not extensively covered in this post, it's worth exploring as an alternative solution.

## Conclusion

The process from encountering compatibility issues to a fully functional Jekyll development environment was certainly a challenging but rewarding experience. Navigating the intricacies of Ruby versions and choosing the right tools allowed me to overcome obstacles and resume local development with confidence.