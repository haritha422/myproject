node('built-in')
{
    stage('download') 
    {
       git 'https://github.com/IntelliqDevops/maven.git' 
    }
    stage('build')
    {
        sh 'mvn package'
    }
    stage('deployment') 
    {
         sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.19.220:/var/lib/tomcat10/webapps/testapp.war'
    }
    stage('testing')
    {
        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('delivery')
    {
         sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.19.243:/var/lib/tomcat10/webapps/prodapp.war'
    }
}

