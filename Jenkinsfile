pipeline {

  agent any

  stages {

    stage('Checkout SCM') {
     steps {
                                git 'https://github.com/riadhmars/CDProjet.git'
                        }
}

stage('Push to Dockerhub'){
    steps {

          script{
          sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
}


}
}
  }
}
