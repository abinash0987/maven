node('built-in')
{
    stage('ContineousDownloads') 
    {
      git 'https://github.com/intelliqittrainings/maven.git'
      
    }
    stage('continuousBuild')
    {
        sh 'mvn package'
    }
    stage('continuousDeployment')
    {
    deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://172.31.24.62:8080')], contextPath: 'testapp', war: '**/*.war'
    }
   stage('continuousTesting')
    {
        git'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    stage('continuousDelivery')
    {
       deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://172.31.18.32:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    
}
    
    
    
    
    
    
}
