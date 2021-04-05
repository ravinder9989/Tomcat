pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
              git branch: 'main',url: "https://github.com/ravinder9989/Tomcat.git" 
              sh "ls -ll"
            }
        }
        stage('playbook') {
            steps {
                ansiblePlaybook credentialsId: 'ansible1_key', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'installing_apache2.yml'
            }
        }
    }
    post {
            success {
                mail to:"nandyalaravinder@gmail.com, ravinder.n@isteer.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
            }
            failure {
                mail to:"nandyalaravinder@gmail.com, ravinder.n@isteer.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
            }
        }
}
