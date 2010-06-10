!SLIDE bullets
# `$ vagrant provision`

!SLIDE center
# Opscode Chef
## Infrastructure Automation for the Masses.™

!SLIDE code
    
    @@@ ruby
    Vagrant::Config.run do |config|
      # ...
      config.vm.provisioner = :chef_solo
      config.chef.cookbooks_path = "cookbooks"
      config.chef.json.merge!(
        :mysql => { 
          :server_root_password => "root"
        }
      )

      config.chef.log_level = :debug
      # ...
    end

!SLIDE bullets
# Examples 
* Many cookbooks available on github.com/opscode/cookbooks
* Example Vagrant project: rails_test_box

