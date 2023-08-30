# PageUp and PageDown history search auto completion on the BASH shell

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


### Afret Change something use just "exec bash"