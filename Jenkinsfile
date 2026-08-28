node('built-in') 
{
    stage('continuousdownload')
    {
        git 'https://github.com/IntelliqDevops/maven.git'
    }
    stage('build')
    {
        sh 'mvn package'
    }
    stage('deploy')
    {
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '70f0605c-67d7-4e10-86d6-3ca27e7d19ae', path: '', url: 'http://172.31.19.220:8080')], contextPath: 'testapp', war: '**/*.war' 
    }
    stage('testing')
    {
        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
        sh 'java -jar testing.jar'
    }
    stage('delivery')
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '70f0605c-67d7-4e10-86d6-3ca27e7d19ae', path: '', url: 'http://172.31.19.243:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
}


