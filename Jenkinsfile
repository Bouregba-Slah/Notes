pipeline{
    environment {
        DOCKERHUB_CREDENTIALS_LOCAL = credentials("DOCKERHUB_CREDENTIALS")

    }
    agent any 
    stages { 
        
        stage('test') {
            steps { 
                sh 'echo $DOCKERHUB_CREDENTIALS_LOCAL_USR' 
                sh 'echo $DOCKERHUB_CREDENTIALS_LOCAL_PSW'
            }
        }
        stage('Docker-compose down build up') {
            steps {
                sh 'docker-compose build backend'
                sh 'docker login -u bouregbaslah -p BouregbaSlah@1987'
                sh 'docker push bouregbaslah/notesbackend:v1'
                
            }
        } 
    }
}