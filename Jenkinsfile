pipeline{
    agent any

    environment{
        ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')
    }
        stages{
            stage("checkout"){
                steps{
                    git "https://github.com/thinkC/flask-app.git"
                }
            }
            // stage("Install zip"){
            //     steps{
            //         ansiblePlaybook credentialsId: 'ansible-access', installation: 'Ansible on jenkins01', inventory: '/var/lib/Jenkins/workspace/Flask App/inventory', playbook: '/var/lib/Jenkins/workspace/Flask App/test.yml', vaultTmpPath: ''
            //     }
            // }
         
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
