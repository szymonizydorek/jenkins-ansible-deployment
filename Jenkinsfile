pipeline {
    agent any

    stages {
        stage('List Files') {
            steps {
                sh 'ls'
            }
        }

        stage('Execute shell') {
            steps {
                sh '''
                    whoami
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
