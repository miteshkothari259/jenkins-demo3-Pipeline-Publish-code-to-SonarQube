node{
   stage('SCM Checkout'){
     git 'https://github.com/sureshchandrarhca15/jenkins-demo3-Pipeline-Publish-code-to-SonarQube.git'
   }

   stage('Compile-Package'){
    //Get Maven Home path
      def mvnHome =  tool name: 'maven_3_5_2', type: 'maven'   
     sh "${mvnHome}/bin/mvn clean install package -Dmaven.test.skip=true"   
   }
   
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven_3_5_2', type: 'maven'   
        withSonarQubeEnv('sonarqube_server') { 
          sh "${mvnHome}/bin/mvn clean install package -Dmaven.test.skip=true sonar:sonar"
    }
   
    stage('Email Notification'){
    mail bcc: '', body: '''Hi,
    The Build Pipeline for "jenkins-demo3-Pipeline-Publish-code-to-SonarQube" Job has been triggered Successfully. 

  Thanks,
  Jenkins Team''', cc: 'sureshchandra.rhca@gmail.com', from: '', replyTo: '', subject: 'Jenkins Email Notification', to: 'sureshchand.rhce@gmail.com'

   }

 }
