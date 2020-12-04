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
         stage('package') {
           steps {
               script {
                   sh 'mvn clean package'
               }
           }
        }
        
     stage('Ansible Deploy') {  
            steps {
                sshagent (credentials: ['tomcat']
                ansiblePlaybook(
                    credentialsId: 'Tomcat-Credentials'
                    inventory: 'dev.inv',
                    installation: 'ansible
                    limit: '172.31.16.217',
                    playbook: 'copyfile.yml
                    extras: ' options and var that you want add for instance verbose mode : -vvv'
                )
            }      
}
}
}
}
