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
        stage('Docker-compose backend') {
            steps {
                sh 'docker-compose build backend'
                sh 'echo $DOCKERHUB_CREDENTIALS_LOCAL_PSW | docker login -u $DOCKERHUB_CREDENTIALS_LOCAL_USR --password-stdin'
                sh 'docker push bouregbaslah/notesbackend:v1'
                
            }
        } 
        stage('Docker-compose frontend') {
            steps {
                sh 'docker-compose build frontend'
                sh 'echo $DOCKERHUB_CREDENTIALS_LOCAL_PSW | docker login -u $DOCKERHUB_CREDENTIALS_LOCAL_USR --password-stdin'
                sh 'docker push bouregbaslah/notesfrontend:v1'
                
            }
        } 
    }
}