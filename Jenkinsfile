pipeline {
    agent any

    stages {
        stage('Deploy using Ansible') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'ubuntu') {
                        sh "ansible-playbook ansible/playbook.yml -i ansible/inventory --limit ubuntu"
                    } else if (env.BRANCH_NAME == 'amazon') {
                        sh "ansible-playbook ansible/playbook.yml -i ansible/inventory --limit amazon"
                    } else {
                        error "Unsupported branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }
    }
}
