
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.define "docker1" do |config|
    config.vm.hostname = 'docker1'
  end
  config.vm.define "db1" do |config|
    config.vm.hostname = 'db1'
  end


  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.sudo = true
    ansible.groups = {
      "dockers" => ["docker1"],
      "dbs" => ["db1"],
      "all_groups:children" => ["dockers", "dbs"]
    }
  end

end
