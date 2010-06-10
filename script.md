INTRO
-----
I'm Jeroen van Dijk currently working for TTY Internet Solutions. I'll give you a short introduction to Vagrant. Vagrant is a command-line utility in Ruby that allows developers to easily build and distribute virtualboxes. In this presentation I will give you an overview of how this works and I'll present some use cases.

INGREDIENTS
-----------
Vagrant has four main ingredients. It is written in Ruby and wraps around Virtualbox which is  Java software. Currently Vagrant needs a base box to get started. This base box is a Virtualbox image with an unix operating system like Ubuntu. These boxes can be generated using vagrant. I'll give  an example later on. Last but not least, Vagrant relies on the ruby library Chef to do the provisioning. Future versions might include Puppet as a provision, but as far as I know no one has written an adapter for Puppet yet.

Virtualbox
----------
Virtualbox is open source virtualization software. It currently runs on Windows, Linux, Macintosh and OpenSolaris hosts and supports are large number of guest operating systems, including several Windows versions, Linux versions and Solaris.

If you have ever used Parallels or VMWare, this is similar but is open source.
## Use cases
Virtualboxes is very useful when you want to distribute some environment. When you take over a project of someone else it often means you need to have to add something to your setup. When you hand over a virtualbox environment everything works the same on any machine, no need for extra software.

Another use case for me is cross browser testing. Virtualbox for example makes it easy to run Windows on Mac OS X or Linux.

Sometimes it is hard to setup a certain configuration, Virtualbox solves this by setting it up once and then you can share that environment. This also yields for legacy projects. What do you when you need maintain a project that runs on some ancient ruby version for example.

The downside of Virtualbox is that it is a complex beast. This is were vagrant comes in, making it a lot simpler.

Vagrant
-------
As said earlier, Vagrant wraps around virtualbox and does all the hard work for us. So how does it work? First we need to have Virtualbox installed. This can be downloaded from the Virtualbox site. I'll give links later. 

The first step is to install the gem. 

Then Vagrant has to download a base box. These boxes are around 400mb, so it can take sometime before you can continue here.

Vagrant init ubuntu creates a vagrantfile which has some basic configuration

To start the box we have to run vagrant up. The first time, this will copy the base box over and will setup the port forwarding and share folders. I'll come to configuration a bit later.

vagrant ssh is the command to use when you want to have command line access to your box.

## Base boxes
There are currently several base boxes available among which different ubuntu and debian versions. If you have any other need you can create your own. There are very clear instructions, but it also possible to change the configuration of a base box and the package that. The latter is easier.

The configuration of the Vagrant boxes goes into a Vagrantfile. Virtualhost has many features and vagrant makes already many of them easily configurable. In this example you see that you configure the name of the box and how much memory it can use. You can also set what folders should be shared with the guest os. This way, when developing, you can edit your files in host os say Mac or Windows while the code is running in a Ubuntu OS.

## Provisioning
Provisioning refers to the setup of additional software and services on the virtualbox. Vagrant provides hook to use it with Chef's command line tools. 

Chef is a story of its own and to summarize it allows you to automate server setup. Here is an example of how a Vagrantfile looks like when using chef. As you can see we have a great level of control. We can also control the log level of Chef for debugging purposes. 

# Examples
I wont go into detail here, but Chef is an interesting part of Vagrant. There are currently already many cookbooks available for a wide range of software. See github for cookbooks. I have worked on a Vagrant project that sets up everything to run the tests for Rails. So this might be a good example to get started. There is also a getting started video available on the Vagrant site.

# My use cases for Vagrant
I have used Vagrant so far to build and distribute both develop as test environments. An example of a test environment is the rails_test_box or . Development e

I have also used it to prototype a production environment locally. So I basically used it to test my chef recipes for production. 

# Future use cases?
The vagrant guys are working on a multi vm functionality in order to simulate a multi server environment. I haven't got the chance to try this out, but it seems very promising.

There have also been some request to be able to deploy your box to EC2. One other intesting idea is to use vagrant to manage remote virtualboxes. So virtualbox will run on a server while you are able to manage them locally. This might also give the possibility to have very thin clients. 

Another interesting development is a project on the Google summer of code which has its aim to integrate Vagrant with the OpenNebula Cloud API (http://socghop.appspot.com/gsoc/student_project/show/google/gsoc2010/opennebula/t127230766138). This will also main that the dependency of Virtualbox will be abstracted away so people can use vagrant to build VMware boxes for instance.

Maybe someone here has ideas for other use cases?

# More info can be found on the following pages

# Ruby rocks, need to say more
# questions?