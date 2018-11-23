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
      sh "docker build -t mytomcat02:latest ."
      echo "Image build complete"
   }
   stage('Docker-Push'){
      sh "docker tag mytomcat02 10.141.0.171:5000/mytom/tom2"
      sh "docker push 10.141.0.171:5000/mytom/tom2"
      echo "Image build complete"
   }
   stage('Kubernetes-Deploy'){
      sh "docker tag mytomcat02 10.141.0.171:5000/mytom/tom2"
      sh "docker push 10.141.0.171:5000/mytom/tom2"
      echo "Image build complete"
   }
   stage('Kubernetes-Deploy'){
      sh "kubectl create -f hello-world-service.yaml"
      sh "kubectl create -f hello-world-deployment.yaml"
   }
   
}


