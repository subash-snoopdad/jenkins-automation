pipeline{
    agent any

    stages{
        stage('checkout'){
            checkout scm
        }
    }

    stage('Execute Script'){
        steps{
            echo "Running the built script..."
            sh 'chmod +x ./build.sh'
            sh './build.sh'

            }
        
        }
    }

post{
    always{
        // captures the build logs to include in the email
        script{
            def jobName = env.JOB_NAME
            def buildNumber = env.BUILD_NUMBER
            def buildStatus = currentBuild.currentResult

            mail to: 'subashm.study@gmail.com',
        }
    }
}
