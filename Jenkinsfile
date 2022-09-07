pipeline {
    agent any
    options {
           ansiColor('xterm')
    }
    parameters {

        choice(name: 'ENV', choices: ['', 'prod', 'dev'], description: '')
        choice(name: 'COMPONENT', choices: ['shipping'], description: '')
        string(name: 'APP_VERSION', defaultValue: '', description: 'APP Version')
    }

    stages {
    stage('Terraform'){
    steps {
    sh '''
         terraform init
         terraform apply -auto-approve -var COMPONENT=${COMPONENT} -var ENV=${ENV} -var APP_VERSION=${APP_VERSION}
         '''
    }
    }
    }

    post {
    always {
        cleanWs()
    }
    }
}