Vagrant.configure("2") do |config|
  config.vm.box = "generic/alpine312"

  config.vm.define "go" do |config|
    config.vm.hostname = "discv5-go.box"
    config.vm.provision "shell", path: "go/setup.sh", privileged: false
    config.vm.provision "file", source: "go/run.sh", destination: "$HOME/bin/run.sh"
    config.vm.provision "file", source: "go/test.sh", destination: "$HOME/bin/test.sh"
    # needs two IPs to run test suite
    config.vm.network :private_network, ip: "192.168.3.22", hostname: true
    config.vm.network :private_network, ip: "192.168.3.23"
  end

  config.vm.define "nim" do |config|
    config.vm.hostname = "discv5-nim.box"
    config.vm.provision "shell", path: "nim/setup.sh", privileged: false
    config.vm.provision "file", source: "nim/run.sh", destination: "$HOME/bin/run.sh"
    config.vm.network :private_network, ip: "192.168.3.31"
  end

  config.vm.define "python" do |config|
    config.vm.hostname = "discv5-python.box"
    config.vm.provision "shell", path: "python/setup.sh", privileged: false
    config.vm.network :private_network, ip: "192.168.3.41", hostname: true
  end

  config.vm.define "rust" do |config|
    config.vm.hostname = "discv5-rust.box"
    config.vm.provision "shell", path: "rust/setup.sh", privileged: false
    config.vm.network :private_network, ip: "192.168.3.51"
  end
end