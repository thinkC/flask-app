// pipeline{
//     agent any

//     environment{
//         ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')
//     }
//         stages{
//             stage("checkout"){
//                 steps{
//                     git "https://github.com/thinkC/flask-app.git"
//                 }
//             }
//             stage("Deploy Flask app"){
//                 steps{
//                     ansiblePlaybook credentialsId: 'ansible-access', installation: 'Ansible on jenkins01', inventory: '/var/lib/jenkins/workspace/Flask-App/inventory', playbook: '/var/lib/jenkins/workspace/Flask-App/flask-webapp.yml', vaultTmpPath: ''
//                 }
//             }
         
//         }
//         post{
//             success{
//                 echo "Checkout successful!"
//             }
//             failure{
//                 echo "Checkout failed!"
//             }
//         }
//     }

///////adding JMeter test plan/////////////


pipeline {
    agent any

    environment {
        ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')
        JMETER_HOME = '/home/vagrant/apache-jmeter-5.4.1'  // Set the path to your JMeter installation
    }

    stages {
        stage("checkout") {
            steps {
                git "https://github.com/thinkC/flask-app.git"
            }
        }

        stage("Deploy Flask app") {
            steps {
                ansiblePlaybook credentialsId: 'ansible-access', installation: 'Ansible on jenkins01', inventory: '/var/lib/jenkins/workspace/Flask-App/inventory', playbook: '/var/lib/jenkins/workspace/Flask-App/flask-webapp.yml', vaultTmpPath: ''
            }
        }

        stage("Run JMeter Tests") {
            steps {
                script {
                    // Example command to run JMeter tests
                    sh "${JMETER_HOME}/bin/jmeter -n -t /var/lib/jenkins/workspace/Flask-App/testplan.jmx -l /var/lib/jenkins/workspace/Flask-App/results.jtl -e -o report"
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}

