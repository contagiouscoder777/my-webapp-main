pipeline {
    agent any
    tools {
        maven "MAVEN_HOME"
    }
    stages {
        stage("Checkout") {
            steps {
                // Provide the Git repository URL here
                git ''
            }
        }
        stage("Build") {
            steps {
                sh 'mvn clean install'
            }
        }
        stage("Deploy") {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'devops', path: '', url: 'http://localhost:7080/manager/html')], contextPath: 'mavenpipeline', war: '**/*.war'
            }
        }
    }
}
