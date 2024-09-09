node('')

{
    stage('ContinuesDownload')
    {
        git 'https://github.com/ganjiniharika3/dev.git'
    }
    stage('ContinuesBuild')
    {
       sh 'mvn package'
    }
    stage('ContinueDeployment')
    {
       deploy adapters: [tomcat9(credentialsId: '91a1ee01-43aa-425e-80f0-1c7e170a7909', path: '', url: 'http://172.31.0.255:8080')], contextPath: 'qapipeline', war: '**/*.war'
    }
    stage('ContinuesTesting')
    {
        git branch: 'main', url: 'https://github.com/ganjiniharika3/testing.git'
        sh 'java -jar /var/lib/jenkins/workspace/java-dev-app/testing.jar'
    }
    stage('ContinuesDelivery')
    {
         deploy adapters: [tomcat9(credentialsId: '3fbea652-e485-4757-910a-51921e22cc87', path: '', url: 'http://172.31.13.221:8080')], contextPath: 'prodpipeline', war: '**/*.war'
    }
    
}
