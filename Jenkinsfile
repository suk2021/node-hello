pipeline {
    agent any
   

      parameters {

//        string(name: 'DBUSER', description: 'Username for login to DB')
//      password(name: 'DBPASSWD', description: 'Password for login to DB')
//        string(name: 'GITUSER', description: 'Username for login to Git')
//        password(name: 'GitPASSWD', description: 'Password for login to Git')
        string(name: 'NODE_ENV', description: 'Node Envionment',defaultValue: 'UI')
//        string(name: 'BranchName', description: 'Branch-name ')

   }
    
stages {
   
          stage("Building Nodejs-app-in") {
            steps {
                  withCredentials([string(credentialsId: 'ansiblekey', variable: 'ansiblekey')]) {

                script {
                   ansiblePlaybook credentialsId: 'ansible-key',  installation: 'ansible', inventory: 'inventory', playbook: '2node.yaml' , extras: '-e NODE_ENV=${params.NODE-ENV}-${BRANCH_NAME} -e branch=${BRANCH_NAME}'
                   
                    }
                }
            }
}
}
}

