pipeline {
    agent any

    stages {
        stage('Detect Target OS') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'ubuntu') {
                        env.TARGET_OS = 'ubuntu'
                    } else if (env.BRANCH_NAME == 'amazon') {
                        env.TARGET_OS = 'amazon'
                    } else {
                        error "Unsupported branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh """
                ansible-playbook ansible/playbook.yml \
                -i ansible/inventory \
                -e target_os=${TARGET_OS}
                """
            }
        }
    }
}

