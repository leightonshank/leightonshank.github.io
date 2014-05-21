# [Atom](http://atom.io) Install on Chrome OS

In the [Atom build instructions for Linux](https://github.com/atom/atom/blob/master/docs/build-instructions/linux.md), Ubuntu 12.04 (precise) is recommended.  Let's go ahead and setup a chroot using [Crouton](https://github.com/dnschneid/crouton).  I prefer to use the 'cli-extra' target.

    sh -e ~/Downloads/crouton -r precise -t cli-extra
    sudo enter-chroot -n precise

And then within the _precise_ chroot, install additional packages needed.  The 'binutils' and 'man-db' packages aren't specifically needed to install Atom, but I've found them handy to install.  Who can get by without `man` or `strings`?

    sudo apt-get install binutils man-db libgtk2.0-dev libnotify-dev libxtst-dev libnss3-dev git-core libgnome-keyring-dev
    
One of the other requirements is node.js v0.10.x.  Ubuntu 12.04 comes with an old version of node (v0.6.x) comes in the _precise_ repos, so you need to install node.js from another repo.  Followed [the install instructions on the node.js site](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager).

    sudo apt-get install python-software-properties
    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs
    
(note: the node.js package manager install page says to install python, g++, and make packages -- but when I ran `apt-get install python g++ make` it said that they were already installed.  it also listed packages that were automatically installed but no longer needed.  ran `sudo apt-get autoremove` to clean them up)

Now that we have the updated version of node.js, let's continue with the Atom build instructions

    git clone https://github.com/atom/atom
    sudo npm config set python /usr/bin/python2 -g
    script/build
    sudo script/grunt install
    
    
    
    
    


