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
        
        stage('Login to Docker Hub') {          
           steps{                          
                sh 'docker login -u bouregbaslah -p BouregbaSlah@1987'    
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