pipeline {
    agent any
   

      parameters {

//      string(name: 'DBUSER', description: 'Username for login to DB')
//      password(name: 'DBPASSWD', description: 'Password for login to DB')
//        string(name: 'GITUSER', description: 'Username for login to Git')
//        password(name: 'GitPASSWD', description: 'Password for login to Git')
//        string(name: 'BranchName', description: 'Branch-name ')
          string defaultValue: 'UI', description: '', name: 'NODE_ENV', trim: false


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

