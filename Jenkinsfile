pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages{
        stage('Pull ansible prerequisites'){
            steps{
                git branch: 'main', credentialsId: 'ecr:eu-central-1:aws-credentials', url: 'https://github.com/ilekicgrid/Ansible-for-jenkins.git'
            }
        }

        stage('Ansible-playbook'){
            steps{
                ansiblePlaybook become: true, becomeUser: 'ubuntu', credentialsId: 'ecr:eu-central-1:aws-credentials', disableHostKeyChecking: true, inventory: 'hosts.yml', playbook: 'sites.yml'
            }
        }
    }
}