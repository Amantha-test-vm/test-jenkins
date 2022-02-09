pipeline {
    agent any 

    environment {
        NEW_VERSION = '1.0.1'
        SERVER_CREDENTIALS = credentpials('server-user-cred')
    }

    // tools {
    //     // maven 'Maven'
    //     // gradel

    // }

    parameters {
        string(deployerName:'Admin', description: 'this is a parameter')
        choice(name: 'VERSION',choices : ['1.0.1', '1.0.2', '1.0.3', '1.0.4']) //this will act like build with parameters
        booleanParam(name: 'executeTest' , defultValue: true, description: '')
    }
    

    stages {
        stage ("who-am-i") {
            steps {
                echo "deployer name ${params.deployerName}"
                echo 'My name is Amantha'
                echo 'This is my first pipeline'
            }
        }

        stage ("build") {
            steps {
                // sh 'npm install'
                echo 'building the application'
                sh 'maven install'
            }
        }

           stage ("test") {

            //    when {
            //        expression {
            //            BRANCH_NAME == 'stage'
            //        }

                   steps {
                       echo 'This is srtage branch'
                       echo '1'
                   }

            steps {
                echo 'testing the application'
                echo '2'
            }

            when {
                expression {
                    params.executeTest == true
                }
            }

            steps {
                echo 'npm install\n Installing npm \n....................\n ................'
            }
        }

           stage ("deploy") {
            steps {
                echo 'deploying the application'
                echo "Deploying with ${SERVER_CREDENTIALS}"
                sh "some scripts ${SERVER_CREDENTIALS}"
                
            }
        }

           stage ("validation") {
            steps {
                echo 'validation the application'
                echo "deployed by ${params.deployerName}"
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
