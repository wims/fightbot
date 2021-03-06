
Fight Bot
=========

MMA/Boxing fight logger and polling script for Eggdrop bots


Requirements
------------

  - Eggdrop 1.6.16+
  - TCL 8.5+
  - Tcllib (for **uri** module)
  - SQLite 3.6.19+


Setup
-----

  1. Install [Eggdrop] 1.6.16+, [TCL] 8.5+, and [Tcllib].
     * Tcllib can usually be installed via most package managers, but if you need to install it manually for the local user, follow the miscellaneous [instructions below](#tcllib).
  2. Install [SQLite] with TCL bindings enabled.
     * Download the [SQLite tarball with TCL bindings][sqlite-tarball]
     * Extract and build the TCL sqlite module (typically in the "tea" directory)
        * Example: `tar -zxvf sqlite*.gz && cd sqlite*/tea && ./configure && make`
     * Create a symlink in the *eggdrop* directory to wherever you installed the .so shared object file from the previous step:
        * Example:  `ln -s libsqlite3.7.11.so tclsqlite3.so`
  3. Copy **fights.tcl** and **util.tcl** to the eggdrop *scripts* directory.
  4. Copy **fights.sql** to the *eggdrop* directory.
  5. Add this line to your eggdrop's config file:  `source scripts/fights.tcl`


Miscellaneous
-------------
<div id="tcllib"></div>

### Installing TCLLIB manually under a local user

  1. Download and extract [tcllib].
  2. Install with:

     ``./installer.tcl -no-apps -no-html -no-nroff -no-examples -pkg-path ~/tcllib``

     * This will install tcllib in your home directory under the directory *tcllib/*.
  3. If you wish to remove everything except the "uri" module, type:

     ``cd ~/tcllib && find * -maxdepth 0 -type d -not -name uri -exec rm -rf {} \;``

  4. Set your TCLLIBPATH to ~/tcllib in your .bashrc or .bash_profile file.
     * Example: `export TCLLIBPATH=~/tcllib`
  5. Log out and log back in (or source your .bashrc file again)


[eggdrop]:        http://www.eggheads.org/downloads/
[tcl]:            http://www.tcl.tk/software/tcltk/download.html
[tcllib]:         http://www.tcl.tk/software/tcllib/
[sqlite]:         http://sqlite.org/download.html
[sqlite-tarball]: http://sqlite.org/sqlite-autoconf-3071100.tar.gz
