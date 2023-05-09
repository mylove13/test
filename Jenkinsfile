pipeline {
    agent {
	label "jenkins-node"

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mylove13/maven.git'
            }
        }
        stage('Build'){
            steps {
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Deploy'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', path: '', url: 'http://192.168.56.12:8080')], contextPath: null, war: 'target/hello-world.war'
            }
        }
    }
  }
} 
