node{
   def docker_image = "mytomcat"
   def tag_name = "hello-world"
   stage('SCM Checkout'){
     git 'https://github.com/kadirsahan/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Docker-Build'){
      
      sh "docker build -t ${docker_image}:${BUILD_NUMBER} ."
      echo "Image build complete"
   }
   stage('Docker-Push'){
      sh "docker tag mytomcat03 ${docker_image}:${BUILD_NUMBER}:5000/${tag_name}"
      sh "docker push ${docker_image}:${BUILD_NUMBER}:5000/${tag_name}"
      echo "Image build complete"
   }
   stage('Kubernetes-Deploy'){
      sh "kubectl create -f hello-world-service.yaml"
      sh "kubectl create -f hello-world-deployment.yaml"
   }
   
}


