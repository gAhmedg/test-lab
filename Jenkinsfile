pipeline {
   agent any

       tools {
        maven "maven-3.8.6"
         }



   stages {
     stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }


            stage('test maven') {

      steps {
                
             sh(script: """
                   
               cd l4/
               mvn  clean package
               cd ..

            """)



            }

            post {
                
                success {
                    junit '**l4/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'l4/target/*.jar'
                }
                  failure {
                 echo "failllllllllllll"
                  }
            }
            }

     // stage('Build Docker') {
     //    steps {
//            sh(script: 'docker images -a')
  //           sh(script: """
    //                
      //          cd l4/
        //        docker images -a
  //              docker build -t jenkins-pipeline5 .
    //            docker images -a
      //          cd ..
// 
   //          """)
//          }
//          post {
//             success {
  //              echo " docker successfully :)"
  //           }
    //         failure {
        //        echo "docker failed   :("
     //        }
         //    }
        //  }

        
         
    }
}


      
      
      
   

