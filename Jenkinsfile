node(){

   stage("Git Checkout"){
      checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Git', url: 'https://github.com/maneeth/rentalcars1.git']]])

   }

   stage("Maven Build"){
   sh "mvn package"
   }

   stage("Upload to nexus"){
  nexusArtifactUploader artifacts: [[artifactId: '$BUILD_ID', classifier: '', file: 'target/RentalCars.war', type: 'war']], 
    credentialsId: 'nexus', groupId: 'prod', nexusUrl: '3.95.134.246:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'rentalcars1', version: '$BUILD_ID'
  
  }

   
}

