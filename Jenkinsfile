pipeline {
    agent {
        node {
            label "jenkins-agent-angular"
        }
    }

    stages {
        stage('Install dependecies') {
            steps {
                git url: "https://github.com/ChristianParodi/jenkins-repo.git", branch: "main"
                echo "Installing..."
                sh "npm i"
            }
        }
        stage('Code analysis') {
            steps {
                echo "Analysing code..."
                sh "tslint -c tsconfig.json 'src/**/*.ts'"
            }
            post {
                failure {
                    echo '-- TSLint Failed! -- Please fix the above warnings/errors.'
                }
                success {
                    echo 'TSLint succeeded!'
                }
            }
        }
    }
}
