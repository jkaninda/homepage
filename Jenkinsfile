pipeline {
    agent any
      environment {
        STACK_NAME = "homepage"
        DEPLOYMENT_FILE = "production.yml"
        IMAGE_NAME= "ghcr.io/benphelps/homepage"
        IMAGE_TAG= "latest"
        SERVICE_NAME = "homepage"
    }              
        stage('Deploy to swarm'){
            steps{
              script{
                   sh "docker stack deploy -c ${DEPLOYMENT_FILE} ${STACK_NAME}"

                   //Update the swarm-manager with the new image
                    sh "docker service update --image ${IMAGE_NAME}:${IMAGE_TAG} ${STACK_NAME}_${SERVICE_NAME}"

              }
            }
        }
        
    }
     /* Cleanup workspace */
         post {
           always {
               deleteDir()
           }
       }
} 
