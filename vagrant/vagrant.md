!SLIDE
# Vagrant
## Building and distributing virtualboxes made easy

!SLIDE commandline incremental

# Example please?
.notes before staring install Virtualbox and run it once!

    $ gem install vagrant
    Successfully installed vagrant-0.3.4
    1 gem installed
    
    $ vagrant box add ubuntu http://files.vagrantup.com/base.box
    Vagrant: Downloading via Vagrant::Downloaders::HTTP...
    Vagrant: Creating tempfile for storing box file...
    Vagrant: Copying box to temporary location...
    Vagrant: Extracting box to /Users/jvandijk/.vagrant/boxes/ubuntu...
    Vagrant: Verifying box...
    Vagrant: Cleaning up downloaded box...

!SLIDE commandline incremental
    $ vagrant init ubuntu
    $ vagrant up
    Vagrant: Importing base VM (/Users/jvandijk/.vagrant/boxes/ubuntu/box.ovf)...
    Vagrant: Persisting the VM UUID (c77c601d-a43a-4939-9dad-068384e35c0f)...
    Vagrant: Matching MAC addresses...
    Vagrant: Running any VM customizations...
    Vagrant: Deleting any previously set forwarded ports...
    Vagrant: Forwarding ports...
    Vagrant: Forwarding "ssh": 22 => 2222
    Vagrant: Clearing previously set shared folders...
    Vagrant: Creating shared folders metadata...
    Vagrant: Booting VM...
    Vagrant: Waiting for VM to boot...
    Vagrant: Trying to connect (attempt #1 of 10)...
    Vagrant: Permissions on private key incorrect, fixing...
    Vagrant: Trying to connect (attempt #2 of 10)...
    Vagrant: VM booted and ready for use!
    Vagrant: Mounting shared folders...
    Vagrant: -- v-root: /vagrant
    
!SLIDE commandline incremental
    $ vagrant ssh
    Welcome to your vagrant instance!
    Last login: Fri Mar 12 02:04:54 2010 from 10.0.2.2
    vagrant@vagrantbase:~$

!SLIDE bullets incremental
# Base boxes
* Several boxes available 
(e.g. Ubuntu, Debian)
* Create your own if needed

!SLIDE code
# Configuration
    @@@ ruby
    # ./Vagrantfile
    Vagrant::Config.run do |config|
      config.vm.box = "ubuntu"

      config.vm.customize do |vm|
          vm.name = "Rails Test Environment"
          vm.memory_size = 256
      end

      config.vm.share_folder('x','/host','/box')
      config.vm.forward_port("web", 80, 8080)
    end


!SLIDE commandline
# Packaging boxes
    $ vagrant package --base my_base_box --include Vagrantfile
    Vagrant: Creating temporary directory for export...
    Vagrant: Exporting VM to /Users/jvandijk/.vagrant/tmp/1275846478/box.ovf...
    Vagrant: Packaging VM into /Users/jvandijk/package.box...
    Vagrant: Packaging additional file: Vagrantfile
    Vagrant: Removing temporary export directory...
    