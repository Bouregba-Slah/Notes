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
                
            }
        }
        stage('Login to Docker Hub') {          
           steps{                          
                sh 'docker login -u $DOCKERHUB_CREDENTIALS_LOCAL_USR -p $DOCKERHUB_CREDENTIALS_LOCAL_PSW'                     
                echo 'Login Completed'      
            }
        } 
        stage('Push Image client to Docker Hub') {         
           steps{                            
               sh 'docker push bouregbaslah/notes:latest'           
               echo 'Push Image Completed'       
         }
        } 
    }
}