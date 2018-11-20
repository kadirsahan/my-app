node{
   stage('SCM Checkout'){
     git 'https://github.com/kadirsahan/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Builded successfully
      Thanks
      Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'ksahan@hurriyetemlak.com'
   }
   stage('Slack Notification'){
       slackSend baseUrl: 'https://hooks.slack.com/services/',
       channel: '#system',
       color: 'good', 
       message: 'Welcome to Jenkins, Slack!', 
       teamDomain: 'hemlak',
       tokenCredentialId: 'slack-my-demo'
   }
}


