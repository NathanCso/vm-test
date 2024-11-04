pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/NathanCso/vm-test.git'
            }
        }

        stage('Install Ansible in Virtual Environment') {
            steps {
                sh '''
                    echo "Updating package lists"
                    apt-get update || { echo "Failed to update package lists"; exit 1; }

                    echo "Installing Python3, pip, and virtualenv"
                    apt-get install -y python3 python3-pip python3-venv || { echo "Failed to install Python3, pip, and virtualenv"; exit 1; }

                    echo "Creating a virtual environment"
                    python3 -m venv ansible_env || { echo "Failed to create virtual environment"; exit 1; }

                    echo "Activating the virtual environment and installing Ansible"
                    source ansible_env/bin/activate && pip install ansible || { echo "Failed to install Ansible in virtual environment"; exit 1; }
                '''
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh '''
                    echo "Activating the virtual environment and running Ansible playbook"
                    source ansible_env/bin/activate && ansible-playbook -i ansible/hosts.ini ansible/playbook.yml
                '''
            }
        }
    }
}
