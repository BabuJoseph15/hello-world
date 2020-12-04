pipeline {
    agent any
    tools
    {
       maven "maven3"
    }
    stages {
      stage('SCM checkout') {
           steps {   
               script {
                   git 'https://github.com/BabuJoseph15/hello-world.git'
               }    
           }
        }
         stage('maven3') {
           steps {
               script {
                   sh 'mvn clean package'
               }
           }
        }
        
     stage('Ansible Deploy') {
             
            steps {
                 
           sh "ansible-playbook credentialsId: 'Tomcat-Credentials', disableHostKeyChecking: true, installation: 'ansible', inventory: 'dev.inv', playbook: 'copyfile.yml'"
}
}
}
}
