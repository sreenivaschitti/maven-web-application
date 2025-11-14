pipeline
{
    agent any

    tools
    {
        maven 'Maven_3.9.7'
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


   }
}