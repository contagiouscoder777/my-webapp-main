pipeline {
    agent any
    tools {
        maven "MAVEN_HOME"
    }
    stages {
        stage("Checkout") {
            steps {
                git 'https://github.com/tahseent/my-webapp.git'
            }
        }
        stage("Build") {
            steps {
                bat 'mvn clean install'
            }
        }
        stage("Deploy") {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'devops', path: '', url: 'http://localhost:7080/manager/html')], contextPath: 'mavenpipeline', war: '**/*.war'
            }
        }
    }
}
