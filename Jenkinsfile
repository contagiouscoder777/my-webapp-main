pipeline{
    agent any
    tool{
        maven "MAVEN_HOME"
    }
    stages
    {
        stage("Checkout"){
        step{
            git ''
        }
        }
        stage("Build"){
        step{
            sh 'mvn clean install'
    }
    }
        stage("Deploy")
        {
            step{
                deploy adapters: [tomcat9(credentialsId: 'devops', path: '', url: 'http://localhost:7080/manager/html')], contextPath: 'mavenpipeline', war: '**/*.war'
            }
}
}}
