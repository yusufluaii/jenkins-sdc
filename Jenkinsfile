pipeline {
    agent none
     triggers {
        pollSCM '* * * * *'
    }
    stages {
        
         stage('Checkout SCM') {
            agent {
                label 'master'
            }
            steps {
                checkout scm
            }
        }
        
        stage('Static Analysis') {
            agent {
                docker { image 'sonarsource/sonar-scanner-cli' }
            }
            steps {
                script {
                  //  env.SONAR_HOST_URL="https://sonarcloud.io"
                    //env.SONAR_LOGIN="8c8dc23b1c6e305c93ed35433f44b367ea487d39"
         sh "sonar-scanner -Dsonar.host.url=http://localhost:9000 -Dsonar.login=   -Dsonar.projectKey=jenkins-ci"
                }
                 
            }
        }
        stage('Build ') {
              agent {
                label 'master'
            }
            steps {
              
                sh 'docker build . -t yusufluai/landingpage:$BUILD_NUMBER'
                sh 'docker push yusufluai/landingpage:$BUILD_NUMBER'
             
               script {
                if ( env.BRANCH_NAME == "main") {
                sh 'kubectl set image deployment/landingpage-deployment landingpage=yusufluai/landingpage:$BUILD_NUMBER -n production' }
                else if ( env.BRANCH_NAME == "staging"){
                    sh 'kubectl set image deployment/landingpage-deployment landingpage=yusufluai/landingpage:$BUILD_NUMBER -n staging'
                }
               }
                
                
            }
        }
    }
}
