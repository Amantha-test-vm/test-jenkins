pipeline {
    agent any 

    stages {
        stage ("who-am-i") {
            steps {
                echo 'My name is Amantha'
                echo 'This is my first pipeline'
            }
        }

        stage ("build") {
            steps {
                // sh 'npm install'
                echo 'building the application'
            }
        }

           stage ("test") {

               when {
                   expression {
                       BRANCH_NAME == 'stage'
                   }

//                    stage {
//                        echo 'This is srtage branch'
//                        echo '1'
//                    }
               }

            steps {
                echo 'testing the application'
                echo '2'
            }
        }

           stage ("deploy") {
            steps {
                echo 'deploying the application'
                
            }
        }

           stage ("validation") {
            steps {
                echo 'validation the application'
            }
        }
    }

    post {
        always {
            echo 'this execute something always if the build is faild'
        }
        success {
            echo 'this will execute when the build is success'
            echo 'Build successfull '
        }
        failure {
            echo 'this will execute when the build is fail'
            echo 'Build failed'
            echo 'when expression is not working'
        }
    }
}
