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
				sh 'docker build -t sudheerdk/reactapp:$BUILD_NUMBER /home/ubuntu/React_Docker';
		   }
		}
	    stage ('Push the image') {
		    steps {
		            sh 'docker push sudheerdk/reactapp:$BUILD_NUMBER'
		    }
	    }
    }
}
