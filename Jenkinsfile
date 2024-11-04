pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/NathanCso/vm-test.git'
            }
        }

        stage('Install Ansible via pip') {
            steps {
                sh '''
                    echo "Updating package lists"
                    apt-get update || { echo "Failed to update package lists"; exit 1; }

                    echo "Installing Python3 and pip"
                    apt-get install -y python3 python3-pip || { echo "Failed to install Python3 and pip"; exit 1; }

                    echo "Installing Ansible using pip"
                    pip3 install ansible || { echo "Failed to install Ansible with pip"; exit 1; }
                '''
            }
        }

        stage('Check Files') {
            steps {
                sh 'ls -la ansible/'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh 'ansible-playbook -i ansible/hosts.ini ansible/playbook.yml'
            }
        }
    }
}

