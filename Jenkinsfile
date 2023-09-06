pipeline
{
    agent any
    stages
    {
        stage('contdownload')
        {
            steps
            {
                git 'https://github.com/renukat1805/newmaven.git'
            }
        }
        stage('contbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('contdeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'eb5c631d-1c20-4474-a62d-63fadab15e74', path: '', url: 'http://172.31.10.248:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('conttesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
            }
        }
        stage('contdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'eb5c631d-1c20-4474-a62d-63fadab15e74', path: '', url: 'http://172.31.14.94:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
        
    }
}
