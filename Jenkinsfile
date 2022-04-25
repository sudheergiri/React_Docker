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
				sh 'docker build -t gosalapradeep/reactapp:$BUILD_NUMBER .';
		   }
		}
    }
}
