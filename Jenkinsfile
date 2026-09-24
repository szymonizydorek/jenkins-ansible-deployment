pipeline {
    agent any

    stages {

        stage('List Files') {
            steps {
                sh '''
                    echo "=== Current directory ==="
                    pwd

                    echo "=== Files ==="
                    ls -la
                '''
            }
        }

        stage('Execute shell') {
            steps {
                sh '''
                    echo "=== Jenkins user ==="
                    whoami
                '''
            }
        }

        stage('Debug Ansible Inventory') {
            steps {
                sh '''
                    echo "=== Inventory file ==="
                    cat inventory.yml

                    echo "=== Ansible inventory ==="
                    ansible-inventory -i inventory.yml --graph
                '''
            }
        }

        stage('Execute Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    credentialsId: 'lab_ansible_jenkins',
                    disableHostKeyChecking: true,
                    installation: 'Ansible',
                    inventory: 'inventory.yml',
                    playbook: 'application_deployment.yaml'
                )
            }
        }
    }
}

