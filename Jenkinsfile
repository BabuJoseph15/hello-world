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
        
        stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
               def tfHome = tool name: 'ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
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
                script {
             sh "ansible-playbook copyfile.yml -i dev.inv --user ansadmin --key-file ~/.ssh/id_rsa"
         }        
}
}
}
}
