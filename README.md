# run-from-docker
Dockerized libraries to not install any package that you need for run any command

## Why?

If you are working with a lot of languages, pieces of software, or just need to run a single command one time
maybe you run in the same troubles as me, having to install a lot of dependencies, libraries and so on
that you will no use never more after running the command. Even you can break your linux install if you
are not sure about what you are doing, or if you are copying commands from any website.

How great will be if i say you that you will never else need to install anything else in your computer
other than docker, and that you will be able to run any piece of software without installing anything
else?

This is why i've created this repo, in it you will find a list of official and custom docker images
available in dockerhub, that just pulling them will allow you to execute anything. 

But not only that, you will be running one word command, and you will be in a complete docker instance with
all what you need, and that if you execute something wrong and it crashes, is not a problem, just run it again.

## How it works

You will run for example `vicpython3`, in any folder, and you will be in a docker instance with that folder
mounted in your curren path, so you can execute anything you need, for example `python myscrypt.py`.

After you finish, just write exit, and the container will be destroyed. It will last only meanwhile you have the
terminal opened. If you need it again, you can run again the command.

You can run more than one instance, as the names are handled by docker, so don't worry about it.

## Installing docker

You can follow any of the guides in the official page, but here i leave you how to install docker in Ubuntu 20+


## Add the commands

As you can see, there is a file named .bashrc, you should only use the content of this file and add to your own
one:

Edit your .bashrc
```
vim /home/${USER}/.bashrc
```

and before the last lines where is PATH=[...] add this project .bashrc content
```
[...]

alias vicpython2="docker run -it --rm --name python2 -v ${PWD}:/app -w /app python:2 /bin/bash"
[...]
alias vicpython3="docker run -it --rm --name python3 -v ${PWD}:/app -w /app python:3 /bin/bash"

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:.
PATH=$PATH:.
```

save the file and reload bash
```
exec bash
```

now go to any folder, and run for example `vicpython3` you will be in a different terminal
```
$  vicpython3
root@04f183afc44d:/app#
```

try to run `python -V` and `ls -l`

you will se the python version and all the files in your current folder.

Now you can run any of the other commands

## All the commands start with vic?

Yes, this is only because like this i can write vic pres tab twice, and you will see all the available ones
i've just used something not common to decrease the possibility of collision, but feel free
to change it to wathever you want.
