pipeline {
    agent any
    environment { 
	    //test webhook
		APP_PORT = '9090'
	}
    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/winston86/jenkins-task1-winston86.git', 
		branch: 'main',
		credentialsId: 'github_creds'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Unit Test') {
            steps {
                 sh 'mvn -B test'
            }
			post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
