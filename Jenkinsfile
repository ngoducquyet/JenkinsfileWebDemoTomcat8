node{
   stage('SCM Checkout'){
     git 'https://github.com/ngoducquyet/SpringWebDemo.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven 3', type: 'maven'   
      sh "${mvnHome}/bin/mvn clean package"
   }
   stage('Deploy to Tomcat'){
      sh 'cp target/*.war /opt/tomcat9/webapps'
      sh 'rm -rf /opt/tomcat9/webapps/springwebdemo'
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
       message: 'Welcome to Jenkins, Slack!'
   }
}
