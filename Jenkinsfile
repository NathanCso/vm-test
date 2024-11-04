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
                    apt-get update
                    apt-get install -y software-properties-common
                    apt-add-repository --yes --update ppa:ansible/ansible
                    apt-get install -y ansible
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
