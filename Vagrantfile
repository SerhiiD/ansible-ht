ENV["LC_ALL"] = "en_US.UTF-8"

Vagrant.configure(2) do |config|
    config.vm.define "lamp01" do |lamp01|
        lamp01.vm.box = "centos/7"
        lamp01.vm.network "forwarded_port", guest: 80, host: 1180
        lamp01.vm.network "forwarded_port", guest: 8080, host: 8080

        lamp01.vm.provider "virtualbox" do |virtualbox|
            virtualbox.name = "lamp01"
        end

        lamp01.vm.hostname = "lamp01"

    end

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "lamp.yml"
        ansible.host_key_checking = false
        ansible.tags = "mysql, httpd, php"
    end

end