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
        stage('Docker-compose down build up) {
            steps {
                sh 'cd backend && docker build -t backend .'
                
            }
        }
        stage('Login to Docker Hub') {          
           steps{                          
                sh 'echo $DOCKERHUB_CREDENTIALS_LOCAL_PSW | docker login -u $DOCKERHUB_CREDENTIALS_LOCAL_USR --password-stdin'                     
                echo 'Login Completed'      
            }
        } 
        stage('Push Image client to Docker Hub') {         
           steps{                            
               sh 'docker push bouregbaslah/NOTES:latest'           
               echo 'Push Image Completed'       
         }
        } 
    }
}