pipeline {
    agent any

    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/devops-uk/DevOpsCodeDemo.git'
            }
        }

        stage('Debug Workspace') {
            steps {
                sh '''
                    pwd
                    ls -l
                '''
            }
        }

        stage('Ansible Syntax Check') {
            steps {
                sh 'ansible-playbook -i dev.inv playbook1.yml --syntax-check'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook -i dev.inv playbook1.yml'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment completed successfully'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
