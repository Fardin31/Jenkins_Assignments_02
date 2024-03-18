pipeline {
    agent any 
    stages {
        stage('Build Docker image in dev') { 
            when{
                branch 'dev'
            }
            steps {
                script {
                def app = docker.build("fardin31/dev:latest")
                docker.withRegistry('https://registry.hub.docker.com/fardin31/dev', 'DOCKER_CRED') {
                app.push()
}   
                }
            }
        }
        stage('Build Docker image in qa') {
            when{
                branch 'qa'
            }
            steps {
                script {
                def app = docker.build("fardin31/qa:latest")
                docker.withRegistry('https://registry.hub.docker.com/fardin31/qa', 'DOCKER_CRED') {
                app.push() 
            }
                }
        }
         post {
        always {
            echo 'Deleting Project now !! '
            deleteDir()
        }
        }
    }
}
}

