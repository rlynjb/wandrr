setup Mac OSX requirements server:

max osx comes with a pre-installed Apache2, PHP, and Mysql. ALL pre-installed can be located at `/usr/bin`.

These pre-installs can be overwritten when we install via Brew. and all brew installs go to `/usr/local/bin`.

We can tell mac osx to use a different path so we can use packages installed by brew

sample scenario would be:

- use brew to install php7 and mysql5.7
- run `which php` to see which path it uses
- it should display `/usr/bin/php`
- set PATH to use directory where brew packages are installed
- [Where can I find the installed package path via brew](http://apple.stackexchange.com/questions/145437/where-can-i-find-the-installed-package-path-via-brew)
- c&p this `export PATH=$PATH:/usr/local/bin` to `/Users/name/.zshrc`
- run `which php` again
- it should display `/usr/local...`
