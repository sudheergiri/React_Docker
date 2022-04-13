pipeline {
    agent any
    

    stages {
        stage('SCM-checkout') {
            steps {

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ongraph-Pradeep/React_Docker']]])
            }
        }
	    stage('build image') {
		   steps {
		        sh 'cp ./* /app';
				sh 'docker build -t gosalapradeep/reactapp:99 .';
				sh 'docker run -d --name container99 -p 80:3000 gosalapradeep/reactapp:99';
		   }
		}
    }
}
