# The module command

Modules are a way to store useful programs on HPCs like nhm01. You can find which modules are currently installed on nhm01 by using this command:

module avail

and install them to your user area like this:

module load \<name of module\>

a module will be removed from your user area when you logout, so you’ll need to reload it when you log in again. 
Alternatively, you can add the appropriate module load command to a file in your home directory called .bash_profile. It’s a text file that comes with all user areas. If you copy that module load command to the section labelled #User specific environment and startup programs, you can ensure that it automatically loads every time you log in.
When you open .bash profile, it should look like this

```
# .bash_profile

# Get the aliases and functions

if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs


```

# Installing new modules
If a program can be easily installed locally, to your area, and you think it is unlikely to be used by many people working on nhm01, then we'd like to ask if you could install it locally if at all possible. If you need assistance with that, send me an email (my address is in the introduction) and I'll help however I can.
If you think a program might be of use to many researchers on nhm01, or if you can't install it in your local area because of permission problems or other concerns, get in touch with me and I'll see if we can arrange an installation of a new module with the HPC_Drift team. Please bear in mind this may take a few weeks, but we will keep you updated of our progress.
