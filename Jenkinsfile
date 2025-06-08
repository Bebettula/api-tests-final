pipeline {
    agent any
    triggers{
        pollSCM('*/1 * * * *')
    }
    stages {
         stage('Check git') {
            steps {
                git url: 'https://github.com/Bebettula/python-greetings.git', branch: 'main'
            }
        }
        stage('build') {
            steps {
                script{
                    buildup()
                }
            }
        }
    }
    
}

def buildup(){
    echo "Building of python application is starting."
    sh "docker build -t betija/api-tests:latest ."
    
    echo "Pushing image to docker registry"
    sh "docker push betija/api-tests:latest"
}