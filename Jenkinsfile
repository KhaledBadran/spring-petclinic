pipeline { 
    agent any
    stages {
        stage('Build') { 
            steps { 
                 bat "./mvnw clean"
            }
        }
        stage ('Test') {
            steps {
                 bat "./mvnw test"              
            }
        }
        stage('Package') { 
            steps {
                 bat "./mvnw package" 
            }
        }
        stage('Deploy') {
                  when {
                       branch 'master'
                  }
                  steps {
                        echo 'Deploying stage has been executed'
                  }
        }
    }
    post {
        success {
            mail to: 'badrankhaled97@gmail.com',
             subject: "The jenkins build is successful ${currentBuild.fullDisplayName}",
             body: "Build${env.BUILD_URL}"
        }
        failure {
           mail to: 'badrankhaled97@gmail.com',
             subject: "The jenkins build is failure: ${currentBuild.fullDisplayName}",
             body: "Build${env.BUILD_URL}"
        }
    }
}