node('master') 
{
    stage ('ContinuousDownload')
{
    git 'https://github.com/intelliqittrainings/maven.git'
}
stage ('ContinuousBuild')
{
   sh 'mvn package' 
}
stage ('ContinuousDeployment')
{
 sh 'scp /home/ubuntu/.jenkins/workspace/ScriptPipeline/webapp/target/webapp.war ubuntu@10.3.0.226:/var/lib/tomcat8/webapps/testapp.war'
}
stage ('ContinuousTesting')
{
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptPipeline/testing.jar'
}
stage ('ContinuousDelivery')
{
    sh 'scp /home/ubuntu/.jenkins/workspace/ScriptPipeline/webapp/target/webapp.war ubuntu@10.3.0.139:/var/lib/tomcat8/webapps/prodapp.war'
}
}
