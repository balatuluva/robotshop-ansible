pipeline {

    agent {
        node {
            label 'workstation'
        }
    }

    parameters {
        choice(name: 'env', choices: ['dev', 'prod'], description: 'pick environment')
        string(name: 'component', defaultValue: '', description: 'component name')
    }

    stages {
        stage('Ansible') {
            steps {
                sh 'ansible-playbook -i ${component}-${env}.gehana26.online, roboshop.yml -e ansible_user=centos -e ansible_password=DevOps321 -e env=${env} -e role_name=${component}'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}