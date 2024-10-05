node('built-in')
{
    stage('ContineousDownloads') 
    {
      git 'https://github.com/abinash0987/maven.git'
      
    }
    stage('continuousBuild')
    {
        sh 'mvn package'
    }
    stage('continuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'new-cred', path: '', url: 'http://172.31.24.144:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuousTesting')
    {
        git'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/Delarativepipeline/testing.jar'
    }
    stage('continuousDelivery')
    {
       deploy adapters: [tomcat9(credentialsId: 'new-cred', path: '', url: 'http://172.31.31.31:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    
}
