node(){

   stage("Git Checkout"){
      checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Git', url: 'https://github.com/maneeth/rentalcars1.git']]])

   }

   stage("Maven Build"){
   sh "mvn package"
   }

  }
