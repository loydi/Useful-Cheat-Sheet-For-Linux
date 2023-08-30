PageUp and PageDown history search auto completion on the BASH shell

From the BASH shell it’s possible to have auto-completion where you start to type in part of a command, and then use a keystroke sequence, such as PageUp or PageDown, to then cycle through the history for commands which started with the first text you have entered.

For example, if the last few commands you had entered at the BASH shell were as follows:

ls -l /
ls -l /home
ls -l /var
ls -l /home/chris
ls -l /var/spool/mail/
The entering ls -l and then PageUp would show all of the previously entered commands starting with ls -l in reverse order, ie the reverse of the items above.

If you entered ls -l /h and PageUp then you’d get ls -l /home/kemal followed by ls -l /home.

It’s then also possible to cycle forward through the commands again using the PageDown key. This is useful if you’d hit the PageUp key a few too many times and need to go back to one of the more recent commands in the history.

The key that is bound to this search forward and search backward history does not necesssarily have to be PageUp and PageDown, but I personally always set it to this as it’s what I am used to.

The file that contains the settings for these BASH key bindings is located at /etc/inputrc, and by default on Debian 5 looks like this:

# /etc/inputrc - global inputrc for libreadline
# See readline(3readline) and `info rluserman' for more information.

# Be 8 bit clean.
set input-meta on
set output-meta on

# To allow the use of 8bit-characters like the german umlauts, uncomment
# the line below. However this makes the meta key not work as a meta key,
# which is annoying to those which don't need to type in 8-bit characters.

set convert-meta off

# try to enable the application keypad when it is called.  Some systems
# need this to enable the arrow keys.
# set enable-keypad on

# see /usr/share/doc/bash/inputrc.arrows for other codes of arrow keys

# do not bell on tab-completion
# set bell-style none
# set bell-style visible

# some defaults / modifications for the emacs mode
$if mode=emacs

# allow the use of the Home/End keys
"\e[1~": beginning-of-line
"\e[4~": end-of-line

# allow the use of the Delete/Insert keys
"\e[3~": delete-char
"\e[2~": quoted-insert

# mappings for "page up" and "page down" to step to the beginning/end
# of the history
# "\e[5~": beginning-of-history
# "\e[6~": end-of-history

# alternate mappings for "page up" and "page down" to search the history
 "\e[5~": history-search-backward
 "\e[6~": history-search-forward

# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

$if term=rxvt
"\e[7~": beginning-of-line
"\e[8~": end-of-line
"\eOc": forward-word
"\eOd": backward-word
$endif

# for non RH/Debian xterm, can't hurt for RH/Debian xterm



### Afret Change something use just "exec bash"