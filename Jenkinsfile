pipeline {
    agent any
	def buildNumber = BUILDNUMBER
    

    stages {
        stage('SCM-checkout') {
            steps {

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ongraph-Pradeep/React_Docker']]])
            }
        }
	    stage('build image') {
		   steps {
		        sh 'cp ./* /app';
				sh 'docker build -t gosalapradeep/reactapp:${BUILDNUMBER} .';
				sh 'docker run -d --name container${BUILDNUMBER} -p 80:3000 gosalapradeep/reactapp:${BUILDNUMBER}';
		   }
		}
    }
}
