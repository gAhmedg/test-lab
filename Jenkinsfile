pipeline {
   agent any

   stages {
     stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Maven Build') {
         steps {

            sh(script: """
                   
            mvn clean test

            """)

            
            
            post {
            success {
               echo "test successfully :)"
            }
            failure {
               echo "test failed   :("
            }
            }
         }

      }

      stage('Build Docker') {
         steps {
           sh(script: 'docker images -a')
            sh(script: """
                   
               cd azure-vote/
               docker images -a
               docker build -t jenkins-pipeline .
               docker images -a
               cd ..

            """)
            post {
            success {
               echo " docker successfully :)"
            }
            failure {
               echo "docker failed   :("
            }
            }
         }
         
      }


      
      
     
      
   }
}
