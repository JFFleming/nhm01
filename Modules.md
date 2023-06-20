# The module command

Modules are a way to store useful programs on HPCs like nhm01. You can find which modules are currently installed on nhm01 by using this command:

module avail

and install them to your user area like this:

module load \<name of module\>

a module will be removed from your user area when you logout, so you’ll need to reload it when you log in again. 
Alternatively, you can add the appropriate module load command to a file in your home directory called .bash_profile. It’s a text file that comes with all user areas. If you copy that module load command to the section labelled #User specific environment and startup programs, you can ensure that it automatically loads every time you log in.
When you open .bash profile, it should look like this

```
\# .bash_profile

\# Get the aliases and functions

if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

\# User specific environment and startup programs


```
