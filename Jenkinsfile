pipeline {
  agent any
  stages {     
    stage("Build") {
            steps {
                sh 'mvn clean test'
               
            }
    }
    stage('Sonarqube Analysis') {
          environment {
              scannerHome = tool 'SonarQubeScanner'
          }
          steps {
              withSonarQubeEnv('sonarqube') {
                  sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=560ed56a592f6302844117ce8f56b4dd7c217beb"
              }
          }
    }
    // stage("Quality Gate") {
    //       steps {
    //           timeout(time: 1, unit: 'MINUTES') {
    //           waitForQualityGate abortPipeline: true }
    //       }
    // }    
  } 
        
  // post {

  //     aborted {

  //       echo "Sending message to Slack"
  //       slackSend (color: "${env.SLACK_COLOR_WARNING}",
  //                 channel: "${params.SLACK_CHANNEL_2}",
  //                 message: "*ABORTED:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.USER_ID}\n More info at: ${env.BUILD_URL}")
  //     } // aborted

  //     failure {

  //       echo "Sending message to Slack"
  //       slackSend (color: "${env.SLACK_COLOR_DANGER}",
  //                 channel: "${params.SLACK_CHANNEL_2}",
  //                 message: "*FAILED:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.USER_ID}\n More info at: ${env.BUILD_URL}")
  //     } // failure

  //     success {
  //       echo "Sending message to Slack"
  //       slackSend (color: "${env.SLACK_COLOR_GOOD}",
  //                 channel: "${params.SLACK_CHANNEL_1}",
  //                 message: "*SUCCESS:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.USER_ID}\n More info at: ${env.BUILD_URL}")
  //     } // success

  // } // post
        
        
}
