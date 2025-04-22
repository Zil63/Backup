
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
Vagrant.configure("2") do |config|
  # Base VM OS configuration.
  config.vm.box = "ubuntu/jammy64"
  # имя пользователя
  #config.ssh.username = 'borg'
  # пароль пользователя
  #config.ssh.password = 'borg'
  # можно подключаться по паролю
  #config.ssh.keys_only = false

  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.cpus = 2
  end

  # Define two VMs with static private IP addresses.
  boxes = [
    { :name => "Backup", 
      :ip => "192.168.56.16",
    },
    { :name => "client",
      :ip => "192.168.56.12",
    }
  ]
  # Provision each of the VMs.
  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
      config.vm.network "private_network", ip: opts[:ip]

    end
  end
end
