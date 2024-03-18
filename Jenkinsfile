pipeline {
    agent any
    environment { 
		APP_PORT = '9090'
	}
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Unit Test') {
            steps {
                 sh 'mvn test'
            }
			post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
