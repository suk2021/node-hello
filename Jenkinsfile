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
                  

                    sh """ 

                     echo ${BRANCH_NAME} ${params.NODEENV}

                     ansible-playbook nodejs.yaml --private-key=${key} -e "\branch=${BRANCH_NAME} NODE_ENV=NODE-ENV-${BRANCH_NAME}\" -vv 
                     """
                    }
                }
            }
}
}
}

