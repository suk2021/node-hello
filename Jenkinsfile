pipeline {
    agent any
   

      parameters {

        string(name: 'DBUSER', description: 'Username for login to DB')
        password(name: 'DBPASSWD', description: 'Password for login to DB')
        string(name: 'GITUSER', description: 'Username for login to Git')
        password(name: 'GitPASSWD', description: 'Password for login to Git')
        string(name: 'NODEENV', description: 'Node Envionment')
        string(name: 'BranchName', description: 'Branch-name ')

   }
    
stages {
   
          stage("Building Nodejs-app-in") {
            steps {
                  withCredentials([string(credentialsId: 'ansiblekey', variable: 'ansiblekey')]) {

                script {
                   ansiblePlaybook credentialsId: 'ansible-key', extras: 'NODE_ENV=NODE-ENV-MASTER', installation: 'ansible', inventory: 'inventory', playbook: '2node.yaml'
                   
                    }
                }
            }
}
}
}
//                     ansible-playbook nodejs.yaml --private-key=${key} -e "\branch=master NODE_ENV=NODE-ENV-master\" -vv 

