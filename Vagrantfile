######################################################################
#                                                                    #
# Vagrant configuration file                                         #
# author: Paweł Chalacis <pchalacis@gmail.com>                       #
# this box contains:                                                 #
# - nodejs                                                           #
# - nginx                                                            #
# - mongodb                                                          #
# - redis                                                            #
######################################################################

Vagrant::Config.run do |config|

    config.vm.customize [
        'modifyvm', :id,
        '--memory', 1024,
        '--cpus',   1
    ]

    config.vm.boot_mode = 'headless'
    config.vm.host_name = "nodeserver"

    config.vm.box = 'centos'

    config.vm.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]

    config.vm.forward_port 22, 2022
    config.vm.forward_port 80, 9000
    config.vm.forward_port 8001, 9001

    config.ssh.max_tries     = 50
    config.ssh.timeout       = 300
    config.ssh.forward_agent = true

    # Enable and configure the chef solo provisioner

    config.vm.provision :chef_solo do |chef|

        chef.cookbooks_path = 'build/cookbooks'

        # chef.add_recipe('apt-get')
        # chef.add_recipe('build-essential')
		# chef.add_recipe('vim')

        chef.add_recipe('git')
        chef.add_recipe('nodejs')
        chef.add_recipe('nginx')
        chef.add_recipe('vim')

        chef.log_level = :info

    end


end