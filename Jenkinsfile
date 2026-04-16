pipeline {
  agent any
    stages {
      stage ("Install Docker") {
        steps {

          sh "sudo yum install docker -y && sudo systemctl start docker && sudo systemctl enable docker && sudo usermod -aG docker $USER && newgrp docker && sudo mkdir -p /usr/lib/docker/cli-plugins && sudo curl -SL https://github.com/docker/compose/releases/latest/download/docker-compose-linux-$(uname -m) -o /usr/lib/docker/cli-plugins/docker-compose && sudo chmod +x /usr/lib/docker/cli-plugins/docker-compose
      }
    }
          
      stage ("Git") {
        steps {
        sh "sudo git clone https://github.com/SM211099/JEN.git"

      }
    }

      stage ("Git") {
        steps {
        sh "sudo git clone https://github.com/SM211099/JEN.git"

      }  
    }
  }
}
