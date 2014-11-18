 # A Virtual Machine for Development using Vagrant

## Introduction
This project automates the setup of a development environment. Use this virtual machine to work on a pull request with everything ready to hack and run the test suites.

## Requirements
* [VirtualBox](https://www.virtualbox.org)

* [Vagrant 1.1+](http://vagrantup.com) (not a Ruby gem)

## How To Build The Virtual Machine
1. **Install Vagrant**, which can be [downloaded](http://www.vagrantup.com/downloads.html) from the Vagrant site, which also provides [step-by-step installation instructions](http://docs.vagrantup.com/v2/getting-started/index.html).

2. **Build the VM**

  In the directory you want to work in, enter the following:

  ```
  $ git clone <URL of this repository>
  $ cd <Name of repository>
  $ vagrant up
  ```

If the base box is not present, `vagrant up` fetches it first.

After the installation has finished (it can take several minutes), you can access the virtual machine with the following command:

    host $ vagrant ssh
    Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)
    
`host $` refers to the command prompt on your computer's OS, as opposed to the prompt in the virtual machine.

If you're on Windows, you can opt to access the virtual machine using an ssh client such as Putty or Bitvise SSH, with the following parameters:

```
Host: 127.0.0.1
Port: 2222
Username: vagrant
Password: vagrant
```

Port 8080 in the host computer is forwarded to port 8080 in the virtual machine. Thus, applications running in the virtual machine can be accessed via localhost:8080 in the host computer.

## What's In The Box
* Git

* RVM

* Ruby 2.1.3 (binary RVM install)

* Bundler

* Postgres

* System dependencies for nokogiri and pg

* Databases and users needed to run the test suite

* Node.js for the asset pipeline

* PhantomJS

## Recommended Workflow
The recommended workflow is

* edit in the host computer (i.e. your physical computer)

and

* test within the virtual machine.

This workflow is convenient because in the host computer you normally have your editor of choice fine-tuned, Git configured, and SSH keys in place.

## Virtual Machine Management

When done just log out with `^D` and suspend the virtual machine

    host $ vagrant suspend

then, resume to hack again

    host $ vagrant resume

Run

    host $ vagrant halt

to shutdown the virtual machine, and

    host $ vagrant up

to boot it again.

You can find out the state of a virtual machine anytime by invoking

    host $ vagrant status

Finally, to completely wipe the virtual machine from the disk **destroying all its contents**:

    host $ vagrant destroy # DANGER: all is gone

Please check the [Vagrant documentation](http://docs.vagrantup.com/v2/) for more information on Vagrant.
