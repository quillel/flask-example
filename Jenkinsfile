node {
     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
         app = docker.build("quillel/flask-example")
     }
     stage('Push image') {
         sh 'rm  ~/.dockercfg || true'
         sh 'rm ~/.docker/config.json || true'

         docker.withRegistry('https://616755845023.dkr.ecr.ap-northeast-2.amazonaws.com/bar', 'ecr:ap-northeast-2:adminuser-ecr-credentials') {
             app.push("${env.BUILD_NUMBER}")
             app.push("latest")
         }
     }
}
