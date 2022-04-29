pipeline {
 agent any
 
 stages {
 stage('SCM-checkout') {
 steps {
 checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], 
userRemoteConfigs: [[url: 'https://github.com/sudheergiri/React_Docker']]])
 }
 }
 stage('pushing the code'){
    steps{
      sh "sudo cp -r . /home/ubuntu/React_Docker/"
}
}
 stage('STOP previous Container') {
 steps {
sh ' docker rm -f $(docker ps -a -q) ';
 }
}
 stage('build new image') {
 steps {
sh ' docker build -t sudheerdk/reactapp:$BUILD_NUMBER /home/ubuntu/React_Docker/';
 }
}
stage('build new conatiner') {
 steps {
sh ' docker run -d --name c-$BUILD_NUMBER -p 80:3000 sudheerdk/reactapp:$BUILD_NUMBER';
sh ' docker run -d --name d-$BUILD_NUMBER -p 3000:3000 sudheerdk/reactapp:$BUILD_NUMBER';
 }
}
 }
}
