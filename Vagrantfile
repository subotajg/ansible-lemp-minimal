# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
Vagrant.configure(2) do |config|
  config.vm.box = "parallels/debian-8.1"

  config.vm.network "private_network", ip: "192.168.13.37"
  config.vm.hostname = "my.local"
  config.hostsupdater.aliases = ["my-domain.local", "my-other-domain.local"]
  config.vm.provider "parallels" do |pr|
	pr.memory = 256
  end

  config.ssh.forward_agent = true

  config.vm.provision "trigger", :option => "value" do |trigger|
      trigger.fire do
        run "provisioning/hostscript.sh"
        run "provisioning/install_roles.sh"
      end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true
    ansible.extra_vars = {
      ansible_ssh_user: 'vagrant',
    }
    #ansible.skip_tags = 'auth,structure,cron'
  end
end
