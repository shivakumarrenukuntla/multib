node('built-in') 
{
    stage('cntdownload_loans') 
    {
    git branch: 'main', url: 'https://github.com/shivakumarrenukuntla/multib.git'
    }
        stage('contbuild_loans')
    {
        sh 'mvn package'
    }
        stage('contdeployment_loans')
        {
            sh '''
ssh ubuntu@172.31.81.88 "sudo mkdir -p /var/lib/tomcat10/webapps/"
scp /home/ubuntu/.jenkins/workspace/spl/webapp/target/webapp.war ubuntu@172.31.81.88:/var/lib/tomcat10/webapps/testpg.war
'''
         }
         stage('conttesting')
         {
             git 'https://github.com/shivakumarrenukuntla/FunctionalTesting.git'
            sh 'java -jar /home/ubuntu/.jenkins/workspace/multib_main/testing.jar'
         }
         stage('contdelivery')
         {
             
             sh 'scp /home/ubuntu/.jenkins/workspace/multib/webapp/target/webapp.war ubuntu@172.31.83.231:/var/lib/tomcat10/webapps/userpg.war'
         }
    }
