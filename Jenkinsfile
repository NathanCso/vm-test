pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/NathanCso/vm-test.git'
            }
        }

        stage('Setup and Install Ansible') {
            steps {
                sh '''
                    echo "Updating package lists"
                    sudo apt-get update || { echo "Failed to update package lists"; exit 1; }

                    echo "Installing Python3, pip, and virtualenv"
                    sudo apt-get install -y python3 python3-pip python3-venv || { echo "Failed to install dependencies"; exit 1; }

                    if [ -d "ansible_env" ]; then
                        echo "Removing existing virtual environment"
                        rm -rf ansible_env
                    fi

                    echo "Creating a virtual environment"
                    python3 -m venv ansible_env || { echo "Failed to create virtual environment"; exit 1; }

                    echo "Activating the virtual environment and installing Ansible"
                    . ansible_env/bin/activate && pip install ansible || { echo "Failed to install Ansible"; exit 1; }

                    echo "Ansible installation completed"
                '''
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh '''
                    echo "Activating the virtual environment and running Ansible playbook"
                    . ansible_env/bin/activate && ansible-playbook -i ansible/hosts.ini ansible/playbook.yml || { echo "Failed to execute playbook"; exit 1; }
                '''
            }
        }
    }
}
