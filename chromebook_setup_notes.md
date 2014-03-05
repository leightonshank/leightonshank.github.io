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
-  libsqlite3-dev^
-  libv8-dev^
-  build-essential
-  curl
-  uuid-runtime (for Inform7)

Also installed [rbenv](https://github.com/sstephenson/rbenv) and [ruby-build](https://github.com/sstephenson/ruby-build).

\* _needed by ruby-build to compile ruby_
^ _needed by rails_

Used ruby-build plugin to rbenv to install ruby 2.1.1 (latest version).  Then installed rails 4.0.3 (latest version) by running 'gem install rails'.  Had to install a few new packages (listed above).  Then setup a hello world program, and had to install a few more packages (also listed above).  Had to uncomment the line for 'therubyracer' JavaScript engine in the stock Gemfile, then run 'build install'.  Needed to install the 'build-essintial' package from apt (above) to get 'therubyracer' to compile (it was looking for g++).

After all of that, ran 'rails server', and then had a rails server running on port 3000, which I was then able to access with Chrome running in Chrome OS.  That's the goal, be able to have a "native" development environment and be able to do complete local development without network access.

Right now I've got it solved for:

-  python
-  go
-  ruby / rails
-  C (and anything else gcc will handle)

Installed these other packages with Debian too:

-  tmux (gotta have my tmux)
   also installed the 'tmuxinator' gem

__Note:  remember that with rbenv you need to run 'rbenv rehash' any time you install something new to get the shims setup right for your new executables.__  Ran into this after installing 'rails' and again with 'tmuximator'.

Also installed [pathogen](https://github.com/tpope/vim-pathogen) for vim.

Installed Inform7 with the [installer](http://inform7.com/download/content/6G60/I7_6G60_Linux_all.tar.gz) downloaded from http://inform7.com/download.  Version was 6G60 as of this install.  Inform7 installs itself into /usr/local with statically linked binaries, so I thought it would be a good candidate to install in the native Chrome OS, but it needs a perl interpreter, so installed it in the Debian chroot.  Interestingly enough, the Inform 7 shell needs 'uuidgen' to create a new story, which is provided in Chrome OS, but not in the Debian install.  Needed to install the 'uuid-runtime' package through apt.




