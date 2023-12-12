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
                sh 'echo "build executado" > package-release'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Fazendo deploy automatico"'
                script {
                    // Adiciona todos os arquivos modificados ao commit
                    sh 'git add .'
                    
                    // Realiza o commit com uma mensagem específica
                    sh 'git commit -m "Atualização automática pelo Jenkins"'
                    
                    // Empurra as alterações para o repositório remoto (neste exemplo, a branch é 'main')
                    sh 'git push origin main'
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
