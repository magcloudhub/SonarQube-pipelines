node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
    git credentialsId: 'Github-ID', url: 'https://github.com/magcloudhub/SonarQube-pipelines.git'
   }
   stage('Build') {
     withMaven(jdk: 'Java', maven: 'Maven') {
       sh 'mvn clean compile'
     }
   }
   stage('Unit Test') {
     withMaven(jdk: 'Java', maven: 'Maven') {
       sh 'mvn test'
     }
   }
  stage('SonarQube Analysis') {
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
      //}
      withMaven(jdk: 'Java', maven: 'Maven') {
          sh ' mvn sonar:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=anilkumarkoduri-github '+ 
             ' -Dsonar.login=551e8b50e5088ca92d90442196831844bcd35bd9 '
          }
      } 
   
    //stage("Quality Gate"){
          //timeout(time: 1, unit: 'HOURS') {
             // def qg = waitForQualityGate()
              //if (qg.status != 'OK') {
                //  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              //}
         // }
     // }
   
    stage('Archival') {
      withMaven(jdk: 'Java', maven: 'Maven') {
       //sh 'mvn package'
     }
   }
     stage('Deploy to Artifactory Repo') {
     }

   
    stage('Deploy to Dev') {
      
   }
   stage('Smoke Test Execution') {
      
   }

    
}
