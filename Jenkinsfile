pipeline {

  agent any

  stages {

    stage('Checkout SCM') {
     steps {
                                git 'https://github.com/riadhmars/CDProjet.git'
                        }
}
stage('Build'){
    steps {

          script{
          sh "npm install --force"
          sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
}


}
}

stage('DockerImage'){
    steps {

          script{
          sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
}


}
}

stage('Push to dockerhub'){
    steps {

          script{
          sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
}


}
}
 stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
        }
      }
    }
stage('Run containes for monitoring'){
     steps {
         script{
		sh "docker-compose up -d"
 		}
           }
}
  }
}i
