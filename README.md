# lab-setup
This repository will give you instructions on how to get your development environment setup

## VirtualBox and Vagrant

Unless you work in a company that dictates the type of computer that you use, you will most likely find yourself on a team that uses a combination of Mac and Windows and Linux. This is certainly true in a university environment. It is for this reason that we use a common development environment for everyone based on Linux. The reason I have chosen Linux is because the future of computing is the Cloud and the Cloud runs on Linux so you will need these skills eventually! ;-)

For taking this course you will need to have VirtualBox and Vagrant installed on your laptop. The good news is that all of the other software that we install will be contaoner in vurtual machines (VMs) and not mess with your laptop at all.

Download and install VirtualBox and then Vagrant (in that order)

Link to [VirtualBox](https://www.virtualbox.org/)

Link to [Vagrant](https://www.vagrantup.com/)

Once these are installed you can test the installtion with this repo.

## A Programmer's Editor (Atom.io)

You will need a _programmers editor_. You will find it difficult to just use any oldm editor. Features like syntax highlighting and code completion will make you life infinitely easier. You don't need an Integrated Development Environment (IDE) but you can certainly use one if you are already familiar with one.

I will be using **Atom.io** as my programming editor in class. It is very much like the popular Sublime Text but unlike Sublime it is 100% free. (Sublime requires that you buy it after the trial period even though it lets you keep using it. As a fellow developer, you should respect the author's work and either buy it or stop using it)

These are the plug-ins that I use in my Atom editor. This is why you will see syntax highlighing for Gerkin and Dockere and other file types. To make your Atom look like mine, use the `apm` command to install these add-ons:

```
apm install atom-ide-ui
apm install autocomplete-python
apm install busy-signal
apm install compare-files
apm install git-time-machine
apm install ide-json
apm install intentions
apm install language-docker
apm install language-gherkin
apm install language-groovy
apm install language-markdown
apm install linter
apm install linter-pylint
apm install linter-ui-default
apm install markdown-preview-plus
apm install markdown-writer
apm install minimap
apm install python-debugger
apm install python-indent
apm install python-nosetests
apm install python-tools
apm install sonarlint
apm install split-diff
apm install teletype
```

## Vagrantfile

The `Vagrantfile` in this project will set up a complete Python 3 development environment for you within a Linux Virtual Machine. It uses a concept called "_Infrastructure as Code_" to build the same VM every time on everyone's computer regardless of host operating system. This is how we will avoid having code work on one person's machine and not on another.
