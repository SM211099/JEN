pipeline {
    agent any
    
    stages {
        stage("Install Docker & Compose") {
            steps {
                sh '''
                    sudo dnf install docker -y
                    sudo systemctl start docker
                    sudo systemctl enable docker
                    
                    # Install Docker Compose Plugin
                    sudo mkdir -p /usr/lib/docker/cli-plugins
                    sudo curl -SL "https://github.com/docker/compose/releases/latest/download/docker-compose-linux-$(uname -m)" -o /usr/lib/docker/cli-plugins/docker-compose
                    sudo chmod +x /usr/lib/docker/cli-plugins/docker-compose
                    
                    # Ensure the jenkins user can access the docker socket
                    sudo chmod 666 /var/run/docker.sock
                '''
            }
        }
          
        stage("Checkout") {
            steps {
                // Remove the folder if it exists to avoid 'already exists' errors
                sh "rm -rf JEN"
                sh "git clone https://github.com/SM211099/JEN.git"
            }
        }

        stage("Deploy with Compose") {
            steps {
                dir('JEN') {
                    // Use -d to run in background so the pipeline can finish
                    sh "sudo docker compose up -d"
                }
            }  
        }
    }
}
