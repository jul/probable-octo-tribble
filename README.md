[alt useless live demo](tty.gif "Demo")

# Secrets

a bash à la virtualenv to handle environment variable (sometimes secrets)


This script is basically a 58 lines wrapper around the muscle of python/activate.sh

    ( PS1="${PRMPT}$PS1" bash --norc -i)

Pay attention to the AS IS clause in the licence. This is a freaking bad idea to use it
if you don't know what you are doing.
    

# Need fullfilled

Offering a rocket launcher to sysadmin so they can shoot themselves a rocket in
their knees.

Real life sysadmin is about boring tasks has deploying and testing.

A quite evilish interface to give parameters to processes is often environment variables.

This has been quite such a bad history of mal-practices that openSSH wisely default to wipe out
ALL environment variables.

But, docker, Makefiles, CLI and a lot of practical tools can accept these variables.

pro: what is in the environment does not appear in the history and command lines and can
be used in stressful environment such as a zoom video call to avoid your password appearing
on the CLI by using commands such as mount -o user=\$USER,pass=\$PASS ...

Con: well if you are on a shared machine, that you don't trust, don't use it.

# how it works

    secrets ~/.secrets/env.sh
    
Will load the exported variables from the script and leave you in a context where they are available and
the prompt will nicely indicate **SEC:env.sh**

Then
    secrets ~/.secrets/prod
    
Will load the exported variables from the script and leav you in a context where they are available and
the prompt will nicely indicate **SEC:env.sh->prod**
Both environment variable being available last arrived being the right value.

    call to exit (or CTRL+D)

will wipe out the variable from the memory and remove one env per layer.

    secrets 

by itself scans the files in ~/.secrets and proposes an interactive pickup menu for the environment.

    secrets prod command user=\$USER pass=\$PASS

will use the environment variables in *~/secrets/prod* to complete the $USER/$PASS (if they are not defined yet)


# roadmap

## actual

none, this is basically a backup

## 1.0.0 


- Adding a pre/post hook to mount/unmount a crypted directory with bash trap (SIGTERM)
- write a list long as an arm of DONT (basically don't use it).
- document why it is cool to have an env in an env (composition)
- post a gif of use in console to be modern
- finish mr_freeze.sh the functional test generator from a shell script to have a test framework.
- stop procrastinating.
