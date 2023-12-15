pipeline{
    agent any

    environment{
        ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')

        stages{
            stage("checkout"){
                steps{
                    git 
                }
            }
         
        }
    }
}