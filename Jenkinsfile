node{
  parameters {
    choice(name: 'CHOICE', choices: ['Yes, Stage Compile-Package ', 'Yes, Step Email Notification' ,'Nope, Run all'], description: 'Do you want stop at stage?')
  }
   stage('SCM Checkout'){
     git 'https://github.com/ngoducquyet/SpringWebDemo.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'M3', type: 'maven'   
      sh "${mvnHome}/bin/mvn clean package"
   }
   stage('Deploy to Tomcat'){
      sh 'sudo cp target/*.war /opt/tomcat/webapps'
      sh 'sudo rm -rf /opt/tomcat/webapps/springwebdemo'
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Quyet''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'ngoducquyet2018@gmail.com'
   }
   stage('Slack Notification'){
       slackSend baseUrl: 'https://ngoducquyet.slack.com/services/hooks/jenkins-ci/',
       channel: '#build',
       color: 'good', 
       message: 'Job PipelineAsCode is completed , Slack!'
   }
}
