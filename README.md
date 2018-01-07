# lab-setup
This repository will give you instructions on how to get your development environment setup

## VirtualBox and Vagrant

Unless you work in a company that dictates the type of computer that you use, you will most likely find yourself on a team that uses a combination of Mac and Windows. This is certainly true in a university environment. It is for this reason that we use a common development environment for everyone based on Linux! ;-)

For taking this course you will need to have VirtualBox and Vagrant installed on your laptop. The good news is that all of the other software that we install will be contaoner in vurtual machines (VMs) and not mess with your laptop at all.

Download and install VirtualBox and then Vagrant (in that order)

[VirtualBox](https://www.virtualbox.org/)

[Vagrant](https://www.vagrantup.com/)

Once these are installed you can test the installtion with this repo.

## Atom.io Editor

I use Atom.io as my editor. This is the editor you will see me use in class. It is very much like the popular Sublime Text but unlike Sublime it is 100% free. (Sublime requires that you buy it after the trial period even though it lets you keep using it.)

These are the plug-ins that I use in Atom. This is why you will see syntax highlighing for Gerkin and other file types. To make sure Atom look like mine, use the `apm` command to install these add-ons.

```
apm install atom-ide-ui
apm install autocomplete-python
apm install compare-files
apm install git-time-machine
apm install intentions
apm install kite
apm install language-docker
apm install language-gherkin
apm install language-markdown
apm install linter
apm install linter-pylint
apm install linter-ui-default
apm install markdown-preview-plus
apm install markdown-writer
apm install minimap
apm install python-debugger
apm install python-indent@1.1.4
apm install python-nosetests
apm install python-tools
apm install split-diff
apm install teletype
```
