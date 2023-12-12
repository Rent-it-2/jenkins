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
                sh "echo 'Starting with Building JAR with Maven'"
                sh "mvn clean package -Dmaven.test.skip=true"
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Fazendo deploy automatico"'
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
