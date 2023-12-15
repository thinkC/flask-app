pipeline{
    agent any

    environment{
        ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')

        stages{
            stage("checkout"){
                steps{
                    git "https://github.com/thinkC/flask-app.git"
                }
            }
         
        }
        post{
            success{
                echo "Checkout successful!"
            }
            failure{
                echo "Checkout failed!"
            }
        }
    }
}