pipeline
{
    agent any
        stages
        {
            stage('continous download')
            {
                steps
                {
              git 'https://github.com/intelliqittrainings/maven.git'
                }
            }
             stage('continous built')
            {
                steps
                {
              sh 'mvn package'
                }
            }
            stage('continous deploy')
            {
                steps
                {
              sh ' scp /home/ubuntu/.jenkins/workspace/declarativepipeline/webapp/target/webapp.war ubuntu@172.31.9.48:/var/lib/tomcat9/webapps/testapp.war'
                }
            }
             stage('continous test')
            {
                steps
                {
             git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
             sh 'java -jar /home/ubuntu/.jenkins/workspace/declarativepipeline/testing.jar'
                }
            }
             stage('continous delivery')
            {
                steps
                {
              sh ' scp /home/ubuntu/.jenkins/workspace/declarativepipeline/webapp/target/webapp.war ubuntu@172.31.7.105:/var/lib/tomcat9/webapps/prodapp.war'
                }
            }
        }
}


