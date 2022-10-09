pipeline {
   agent any

   stages {
     stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
   //   stage('Maven Build') {
   //      steps {
   //         
   //         sh(script: """
   //               
    //        mvn clean test

     //       """)

            
            
   //      post {
 //       success {
  //         echo "test successfully :)"
   //      }
   //       failure {
  //         echo "test failed   :("
  //       }
//       }
 //     }

   //}

      stage('Build Docker') {
         steps {
           sh(script: 'docker images -a')
            sh(script: """
                   
               cd l4/
               docker images -a
               docker build -t jenkins-pipeline5 .
               docker images -a
               cd ..

            """)
         }
         post {
            success {
               echo " docker successfully :)"
            }
            failure {
               echo "docker failed   :("
            }
            }
         }

         stage('Build') {
            steps {
                
            
                   
            sh   "cd l4/"
            sh   "mvn -Dmaven.test.failure.ignore=true clean package"

            
         }
                  

             
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
         
      }


      
      
      
   

