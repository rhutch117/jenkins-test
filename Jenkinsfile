def camunda_url = [
    'Development': 'localhost:8080',
]

pipeline {
    agent any

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

        stage('Test REST requests') {
            steps {
                script {
                    def calendar_url = "https://calendarific.com/api/v2/holidays?&api_key=758f54db8c52c2b500c928282fe83af1b1aa2be8&country=IN&year=2020"
                    def curl_output = sh returnStdout: true, script: "curl -s ${calendar_url}"
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