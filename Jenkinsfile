node(){

   stage("Git Checkout"){
      checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Git', url: 'https://github.com/maneeth/rentalcars1.git']]])

   }

   stage("Maven Build"){
   sh "mvn package"
   }
  
   

    stage("Sonar Analysis"){
       scannerHome = tool 'sonarqubescanner'
       withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
           
        }
       timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }


  }
