Chrome OS
---------

On Chromebook itself just did the 'dev_install', and then:

-  tmux

Base dev_install will give you 'python' as a language within Chrome OS itself.  Also installed [Go](http://golang.org), since Google made it pretty simple to install within Chrome OS.  This [guide](http://golang.org/doc/install#tarball) was useful.  Also had to mount /home/chronos/user and /tmp as 'exec' to get it to work.

This link was useful too:

https://sites.google.com/site/chromeoswikisite/home/what-s-new-in-dev-and-beta/shell-acess-with-verified-boot

It laid out the basics theory of running a "guest" OS within a chroot.

Guest OS (Debian via crouton)
-----------------------------

After installing Debian _wheezy_ using  [crouton](https://github.com/dnschneid/crouton).  After creating a chroot using the 'cli-extra' target, installed these packages:

-  git
-  vim
-  gcc*
-  make*
-  libssl-dev*

Also installed [rbenv](https://github.com/sstephenson/rbenv) and [ruby-build](https://github.com/sstephenson/ruby-build).

\* _needed by ruby-build to compile ruby_



