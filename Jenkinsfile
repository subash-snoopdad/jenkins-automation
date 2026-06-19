pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Execute Script') {
            steps {
                echo 'Running the build script...'
                sh 'chmod +x ./build.sh'
                sh './build.sh'
            }
        }
    }

    post {
        always {
            script {
                def jobName = env.JOB_NAME
                def buildNumber = env.BUILD_NUMBER
                def buildStatus = currentBuild.currentResult
                
                mail to: 'subashm.study@gmail.com',
                     subject: "Jenkins Build ${buildStatus}: ${jobName} #${buildNumber}",
                     body: "The Jenkins build status is: ${buildStatus}.\n\nCheck the console output here: ${env.BUILD_URL}"
            }
        }
    }
}
