pipeline 
{
    agent any
    stages
    {
        stage('ContinousDownload') 
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/maven.git' 
            }    
        }
        stage('ContinousBuild') 
        {
            steps
            {
               sh 'mvn package' 
            }    
        }
        stage('ContinousDeployment') 
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '13ff49a7-3658-42b0-81d0-f82c2b3a7b32', path: '', url: 'http://172.31.10.76:8080')], contextPath: 'mytestapp', war: '**/*.war' 
            }    
        }
        stage('ContinousTesting') 
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/decleretivepipeline/testing.jar'
            }    
        }
        stage('ContinousDelivery') 
        {
            steps
            {
              input message: 'bhaijan approve to dedo...................', submitter: 'sai'
              deploy adapters: [tomcat9(credentialsId: '13ff49a7-3658-42b0-81d0-f82c2b3a7b32', path: '', url: 'http://172.31.15.7:8080')], contextPath: 'myprodapp', war: '**/*.war' 
            }    
        }
    }
}
