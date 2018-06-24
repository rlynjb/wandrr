---
layout: post
title: "Useful Vim, Tmux, and Linux Commands"
date: 2018-06-16 14:00:48
tags:
- linux
- tmux
- vim
---

# Vim

Key bind: `ctrl + w`.

- Open terminal in vertical pane, `:vert terminal`.
- Open terminal as of version 8, `:term`.
- Open directory tree view, `:E` or `:Ex`
- Go through windows on forward, `gt`.
- Go through windows on backward, `gT`.
- Open a pane vertically, `:vsplit`.
- Resize horizontal pave, `:resize 10`.
- Resize vertical pane, `:vertical resize 10`
- Navigate through split panes, `ctrl + w ` and `hjkl`.

Some basic to advance vim config

- [Vim Config - Simple and Sane Config](http://vimconfig.com/)
- [Vim is the Perfect IDE](https://dev.to/allanmacgregor/vim-is-the-perfect-ide-e80)

-----

# Tmux

Key bind: `ctrl + b`.

- List active tmux, `tmux -ls`
- Attach to an active tmux, `tmux attach -t 0`
- Detach from tmux, `tmux detach`
- Remove a tmux pane, `exit`
- Open a pane vertically, `ctrl + b` and `%`
- Open a pane horizontally, `ctrl + b` and `"`
- Navigate through panes, `ctrl + b` and `arrows keys, up, down, left, right`
- Resize pane, `ctrl + b` and `:resize-pane -L 40`.
- Rename window, `ctrl + b` and `:rename-window nameOfWindow`.

-----

# Linux

### Changing user accounts

- [sudo su commands](https://help.ubuntu.com/community/RootSudo)

### Searching

- [find](https://help.ubuntu.com/community/find)
- [locate]()
- [grep](https://help.ubuntu.com/community/grep)

### Sorting files

- [ls]()
- [ll]()
- Sort files in date `ll -tr` to check which files has been modified recently
- Check for any suspicious injected files

### SSH and SCP

scp with port

`scp -P 21 root@myhost /home/direc/file.tar username@secondhost:/home/dir`

Where -P stands for port number

### Compress and Extract

- compress: `tar -czf folder.tar.gz folder`
- extract: `tar -xzf folder.tar.gz`

### NPM and Nodejs

Use NVM when managing different nodejs and npm versions on a server. Saves time!

### Checking for CPU or Port processes

Use `htop` or `top` commands

- [htop]()
- [top]()

Check for an open port by `ps aux | grep jekyll`.
Kill a process or port by `kill -9 PID#`.
