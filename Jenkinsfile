pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                script{
                sh 'echo "build executado" > package-release'
                // Adiciona todos os arquivos modificados ao commit
                    sh 'git add .'
                sh 'git -c "user.name=$GIT_COMMITTER_NAME" -c "user.email=$GIT_COMMITTER_EMAIL" commit -m "Atualização automática pelo Jenkins"'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Fazendo deploy automatico"'
                script {
                    // Empurra as alterações para o repositório remoto (neste exemplo, a branch é 'main')
                    sh 'git push -u origin main'

                   // sh 'git push origin main'
                }
            }
        }
        stage('Testes') {
            steps {
                sh 'echo "Sucess!"'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
