# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

["vagrant-hostsupdater", "vagrant-hostsupdater"].each do |plugin|
  unless Vagrant.has_plugin?(plugin)
    raise "#{plugin} plugin is not installed"
  end
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "ansible-lamp" do |box|
    box.vm.hostname = "ansible-lamp.local"
    box.vm.box = "boxcutter/ubuntu1404"

    box.vm.provider :vmware_fusion do |vmware|
      vmware.vmx["memsize"] = 1024
      vmware.vmx["numvcpus"] = 2
    end

    box.vm.provider :virtualbox do |vb|
      vb.customize [
        "modifyvm", :id,
        "--memory", "1024",
        "--cpus", 2
      ]
    end

    box.vm.synced_folder ".", "/var/www/ansible-lamp.local/", :type => "nfs"
    box.vm.network :private_network, :auto_network => true
    box.hostsupdater.aliases = ["mailcatcher.ansible-lamp.local"]
    box.hostsupdater.remove_on_suspend = true;

    box.ssh.forward_agent = true
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/lamp.yml"
    ansible.groups = {
      "dev:children" => ["dev-sql", "dev-web"],
      "dev-sql" => ["ansible-lamp"],
      "dev-web" => ["ansible-lamp"]
    }
  end
end
