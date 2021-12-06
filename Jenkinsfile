@Library('Jenkins-Shared-Library')_

// Bucket where the state file lives
def camunda_url = [
    'Development': 'localhost:8080',
]

pipeline {
    agent { label 'build' }
    options {
        timestamps()
        ansiColor('xterm')
        buildDiscarder(logRotator(numToKeepStr: '50', artifactNumToKeepStr:'50'))
    }

    parameters {
        // Creates a Dropdown for Environment Selection
        choice(name: 'environment', choices: 'Development\nTest\nQA\nUAT\nProduction\nDR', description: 'Environment to Deploy')
        string(name: 'MAJOR_VERSION', defaultValue: '1')
        string(name: 'MINOR_VERSION', defaultValue: '0')
        string(name: 'PATCH_VERSION', defaultValue: '0')
    }

    stages {
        stage('Test Jenkins build') {
            steps {
                script {
                    echo "Building ${params.environment}"
                    echo "Using ${camunda_url[params.environment]}"
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}