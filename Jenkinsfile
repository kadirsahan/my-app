node{
   def docker_image = "mytomcat"
   def tag_name = "hello-world"
   def image_repository = "10.141.0.171:5000"
   stage('SCM Checkout'){
     git 'https://github.com/kadirsahan/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Docker-Build'){
      
      sh "docker build -t ${image_repository}/${tag_name}:${BUILD_NUMBER} ."
      echo "Image build complete"
   }
   stage('Docker-Push'){
      sh "docker push ${image_repository}/${tag_name}:${BUILD_NUMBER}"
      echo "Image push complete"
   }
}
