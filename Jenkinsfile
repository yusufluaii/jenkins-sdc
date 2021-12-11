pipeline{
    agent master
    triggers{
        pollSCM '* * * * *'
    }
    stages{
        stage("Testing"){
            agent {
                docker {image 'sonarsource/sonar-scanner-cli'}
            }
            steps{
                script{
                    sh "sonar-scanner -Dsonar.host.url=http://13.250.101.58/ -Dsonar.login=ce00cfa3d163f71332e617dc4715f8e450052ddd   -Dsonar.projectKey=jenkins-ci"
                }
            }
            }
        }
    }