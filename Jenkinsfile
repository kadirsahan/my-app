node{
   stage('SCM Checkout'){
     git 'https://github.com/kadirsahan/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Docker-Build'){
      sh "docker build -t mytomcat01:latest ."
      echo "Image build complete"
   }
   
}


