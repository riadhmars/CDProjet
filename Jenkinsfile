pipeline {

  agent any

  stages {

    stage('Checkout SCM') {
     steps {
                                git 'https://github.com/riadhmars/CDProjet.git'
                        }
}
 stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
        }
      }
    }
  }
}
