pipeline {
	agent any
	stages {
		stage('Checkout') {
                    steps {
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ilekicgrid/Ansible-for-jenkins.git']]])

                  }
                }

            stage('Start application with Ansible') {
                        steps {
                            script {
                                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'key-ssh', disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts.yml', playbook: 'sites.yml'
                            }
                        }
                    }
	}
}
