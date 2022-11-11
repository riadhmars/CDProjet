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
          sh "run npm install --legacy-pear-deps"
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


stage('Push to Dockerhub'){
    steps {

          script{
          sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
}


}
}
  }
}
