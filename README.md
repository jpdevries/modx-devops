# Vagrant setup for MODX with Apache, PHP, MySQL, xdebug

You can install this repository by running the following commands:

```bash
git clone https://github.com/silentworks/modx-devops.git
cd modx-devops
vagrant up
```

Once Vagrant provisioning is successful, you can then navigate to http://192.168.33.121/manager in your web browser.

### Manager Login Info

- username: vagrant
- password: vagrant

### Database Info

- username: vagrant
- password: vagrant
- database name: default


### Manager Contribution Workflow for Frontend Developers

This setup will provide you with a simple setup in order to contribute to the Manager UI, the project is currently using
GruntJS build tool along with SASS and a few other third party libraries. The aim of this repository is to make this workflow
a much easier one than it currently is.

This repository was created to bundle all dependencies into a Vagrant (VirtualBox) setup.

Before we get started, you will require only 2 dependencies.

[Vagrant][] and [VirtualBox][]

Once you have these two setup, you can proceed to the next steps.

#### Step 1
First, clone a copy of this git repo by running:

```bash
git clone -b manager git://github.com/silentworks/modx-devops.git
```

Open this project in your favourite TextEditor/IDE, then edit the Vagrantfile, change repo to your fork of the 
MODX repository. This step is necessary in order to send in Pull Requests.

### Windows users only, OSX users skip to next step

We are making use of symlink in the project because of the way how Grunt works, in order to get this to work on Windows
you will need to do some extra steps first.

You will need to open your cmd prompt in Administrator mode and run the following

```bash
fsutil behavior set SymlinkEvaluation L2L:1 R2R:1 L2R:1 R2L:1
```

#### Step 3 
Now we do:

```bash
cd manager
vagrant up
```

#### Step 4

Once all this is done and the Vagrant box is up and running, you will need to ssh into the box and start using the grunt workflow.

```bash
vagrant ssh
cd /vagrant/www/_build/templates/default
```

Now lets get Bower dependencies:

```bash
grunt build
```

Now lets start watching the filesystem for changes

```bash
grunt
```

And thats it, go on and edit your SASS files and watch grunt run each time you make a save.

[Vagrant]: http://www.vagrantup.com/
[VirtualBox]: https://www.virtualbox.org/