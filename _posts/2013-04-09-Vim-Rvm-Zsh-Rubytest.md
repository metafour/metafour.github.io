---
layout: post
title: Vim, Rvm, Zsh and Rubytest
time: '17:02:41'
day: 09
month: April
year: 2013
---

If [vim-rubytest.vim](https://github.com/janx/vim-rubytest) is using the system
ruby when you want it to use the current rvm zsh may be at fault. On OS X
rename `/etc/zshenv` to `/etc/zshrc`.
