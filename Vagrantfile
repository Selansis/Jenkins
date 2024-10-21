# Vagrantfile for Jenkins setup with additional IP addresses

Vagrant.configure("2") do |config|
  # Define the VM box
  config.vm.box = "ubuntu/jammy64"


  # Private network IPs
  config.vm.network "private_network", ip: "192.168.56.10"

  # Provisioning with shell script
  config.vm.provision "shell", inline: <<-SHELL
    # Update the package list and install Java
    sudo apt-get update
    sudo apt-get install -y openjdk-11-jdk

    # Add the Jenkins key and repository
    wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
    echo "deb http://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list

    # Install Jenkins
    sudo apt-get update
    sudo apt-get install -y jenkins

    # Start Jenkins service
    sudo systemctl start jenkins
    sudo systemctl enable jenkins
  SHELL
end