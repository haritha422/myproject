pipeline
{
    agent any
    stages
    {
        stage('download')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('deploy')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/declarativepipeline1/webapp/target/webapp.war ubuntu@172.31.19.220:/var/lib/tomcat10/webapps/testapp.war'
            }
        }
        stage('testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline1/testing.jar'
            }
        }
        stage('delivary')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/declarativepipeline1/webapp/target/webapp.war ubuntu@172.31.19.243:/var/lib/tomcat10/webapps/prodapp.war'

            }
        }
    }
}
