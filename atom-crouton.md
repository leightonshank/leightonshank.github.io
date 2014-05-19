# [Atom](http://atom.io) Install on Chrome OS using Crouton

First I tried to install Atom in my Debian _wheezy_ chroot, but that didn't work out.  Atom required
glibc 2.14/2.15 and _wheezy_ only has glibc 2.13.  These were the steps to install Atom (the dependencies
were determined by trial-and-error, and are consolidated here for convenience).

  $ sudo apt-get install libgtk2.0-dev libnotify-dev libxtst-dev libnss3-dev
  $ git clone https://github.com/atom/atom.git
  $ cd atom
  $ sudo script/grunt install
  $ sudo script/mkdeb
  $ atom
  
So I created an Ubuntu _trusty_ (14.04 LTS) chroot.  Tried to check the version of glibc on there, but found
that the crouton 'cli-extra' install is missing the `strings` command.  Installed 'binutils'.

  $ sudo apt-get install binutils
  
Also noticed that 'man' wasn't in the chroot, so installed the 'man-db' package

  $ sudo apt-get install man-db
  
Now that we can check the glibc version

  $ strings /lib/x86_64-linux-gnu/libc.so.6 | grep glibc
  glibc 2.19

So _trusty_ has glibc 2.19.  Let's see if that will work to run Atom.
