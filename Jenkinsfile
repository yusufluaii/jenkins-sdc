pipeline{
    agent none
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        agent{
            label 'master'
        }
        stage("Checkout"){
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