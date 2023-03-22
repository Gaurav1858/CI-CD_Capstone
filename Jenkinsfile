pipeline{
    agent any
    stages{
        stage("Development"){
            when {
                branch 'Development'
            }
            steps{
                echo "In Development environment"
                sh '''
                  javac EmployeeInfo.java
                  '''
                echo "Build Successfully!"
            }
        }
        stage("Testing"){
            //when {
                //branch 'testing'
            }
            steps{
                echo "In testing environment"
                sh '''
                  javac EmployeeInfo.java
                  java EmployeeInfo
                  '''
            }
        }

        stage("Production"){
            when {
                branch 'Production'
            }
            steps{
                echo "Deploying to Production environment"
            }
        }
    }
    post {
           failure {
               emailext attachLog:true, body: 'Pipeline is failed!', subject: 'Post Build Action Email', to: 'gaurav.shukla@knoldus.com'
        }
        success {
               emailext attachLog:true, body: 'Build Successfull!!', subject: 'Post Build Action Email', to: 'gaurav.shukla@knoldus.com'
        }
      }
}
