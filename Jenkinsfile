node{
   stage('SCM Checkout'){
     git 'https://github.com/sureshchandrarhca15/jenkins-demo3-Pipeline-Publish-code-to-SonarQube.git'
   }

   stage('Compile-Package'){
    //Get Maven Home path
      def mvnHome =  tool name: 'MAVEN_HOME', type: 'maven'   
     sh "${mvnHome}/bin/mvn clean install package -Dmaven.test.skip=true"   
   }
   
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'MAVEN_HOME', type: 'maven'   
        withSonarQubeEnv('sonarqubeserver') { 
          sh "${mvnHome}/bin/mvn clean install package -Dmaven.test.skip=true sonar:sonar"
    }
   }
    

 }
