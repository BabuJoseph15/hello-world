pipeline {
    agent any
    
    tools
    {
       maven "maven3"
    }
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/BabuJoseph15/hello-world.git'
             
          }
        }
         stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
               def tfHome = tool name: 'Ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
        }
     
        
         stage('maven3') {
           steps {
             
                sh 'mvn package'             
          }
        }
        
     stage('Ansible Deploy') {
             
            steps {
                 
           sh "ansible-playbook main.yml -i inventories/dev/hosts -- user jenkins --key-file ~/.ssh/id_rsa"
}
}
}
}
