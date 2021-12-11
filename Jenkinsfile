pipeline{
    agent none
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage("Checkout"){
            agent {
                label 'master'
            }
            steps{
                echo "Hello Jenkins"
            }
        }
        stage("Build"){
            steps{
                echo "Hello Jenkins"
            }
        }
        stage("Test"){
            steps{
                echo "Hello Jenkins"
            }
        }
        stage("Deploy"){
            steps{
                echo "Hello Jenkins"
            }
        }
    }
    
}