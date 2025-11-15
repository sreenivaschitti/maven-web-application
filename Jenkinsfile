pipeline
{
    agent any

    tools
    {
        maven 'Maven_3.9.7'
    }

    environment{
        buildNumber = "${BUILD_NUMBER}"
    }
   stages{
    
            stage('Git Checkout')
            {

                steps()
                {
                    git branch: 'Devops_test', url: 'https://github.com/sreenivaschitti/maven-web-application.git'
                }
            
            }

            stage('Build Project')
            {
                steps()
                {
                    sh 'mvn clean package'
                }
            }

            stage('Build Docker image')
            {
                steps()
                {
                    sh 'docker build -t sreenivaschitti/dockerpipeline:${buildNumber} .'
                }

            
            }

            stage('Push docker image to docker hub')
            {
                steps()
                {
                  withCredentials([string(credentialsId: 'dockerhubpassword', variable: 'dockerhubpassword')]) 
                  {
    
                    sh 'docker login -u sreenivaschitti -p ${dockerhubpassword}'
                    
                    }  

                    sh 'docker push sreenivaschitti/dockerpipeline:${buildNumber}' 
                }
            }

            stage('delete dockerimage')
            {

                step()
                {
                    sh 'docker rmi -f sreenivaschitti/dockerpipeline:${buildNumber}'
                }

            }


   }
}