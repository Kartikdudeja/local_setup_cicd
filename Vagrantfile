
servers=[
    {
        ### Jenkins Server ###
        :hostname => "jenkins-server",
        :box => "ubuntu/bionic64",
        :ip => "10.3.20.11",
        :memory => "2048",
        :cpu => "2",
        :vmname => "JenkinsServer",
        :script => "./jenkins.sh"
    },
    {
        ### Nexus Server ###
        :hostname => "nexus-server",
        :box => "geerlingguy/centos7",
        :ip => "10.3.20.12",
        :memory => "2048",
        :cpu => "2",
        :vmname => "NexusServer",
        :script => "./nexus.sh"
    },
    {
        ### Sonarqube Server ###
        :hostname => "sonar-server",
        :box => "ubuntu/bionic64",
        :ip => "10.3.20.13",
        :memory => "2048",
        :cpu => "2",
        :vmname => "SonarServer",
        :script => "./sonar.sh"
    },
    {
        ### App Server ###
        :hostname => "app-server",
        :box => "ubuntu/bionic64",
        :ip => "10.3.20.14",
        :memory => "2048",
        :cpu => "2",
        :vmname => "Staging-App-Server",
        :script => "./blank.sh"
    }
]

Vagrant.configure("2") do |config|

  # manages the /etc/hosts file on guest machines in multi-machine environments
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

  servers.each do |machine|
  
      config.vm.define machine[:hostname] do |node|

          node.vm.box = machine[:box]
          node.vm.hostname = machine[:hostname]
          node.vm.network :private_network, ip: machine[:ip]
  
          node.vm.provider :virtualbox do |vb|

              vb.customize ["modifyvm", :id, "--name", machine[:vmname]]
              vb.customize ["modifyvm", :id, "--memory", machine[:memory]]
              vb.customize ["modifyvm", :id, "--cpus", machine[:cpu]]

              # fix for slow network speed issue
              vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
              vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]

          end # end provider

          node.vm.provision "shell", path: machine[:script]

      end # end config
  end # end servers each loop
end
