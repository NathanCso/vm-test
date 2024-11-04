pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/NathanCso/vm-test.git'
            }
        }

        stage('Install Ansible') {
            steps {
                sh '''
                    echo "Updating package lists"
                    apt-get update || { echo "Failed to update package lists"; exit 1; }

                    echo "Installing software-properties-common"
                    apt-get install -y software-properties-common || { echo "Failed to install software-properties-common"; exit 1; }

                    echo "Adding Ansible repository"
                    apt-add-repository --yes --update ppa:ansible/ansible || { echo "Failed to add Ansible repository"; exit 1; }

                    echo "Installing Ansible"
                    apt-get install -y ansible || { echo "Failed to install Ansible"; exit 1; }
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
