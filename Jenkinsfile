def camunda_url = [
    'Development': 'localhost:8080/engine-rest',
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
        stage('Get pwd') {
            steps {
                sh '''
                    ls -lah
                '''
            }
        }
        // stage('Publish') {
        //     environment {
        //         CAMUNDA_URL = "${camunda_url[params.environment]}"
        //         CAMUNDA_USER = "demo"
        //         CAMUNDA_PW = "demo"
        //     }
        //     steps {
        //         sh '''
        //         curl --location --request POST 'localhost:8080/engine-rest/deployment/create' \
        //              --header 'Content-Type: multipart/form-data' \
        //              --header 'Authorization: Basic ZGVtbzpkZW1v' \
        //              --form 'upload=@"/Users/ryanhutchison/Downloads/invoice.v2.bpmn"'
        //         '''
        //     }
        // }
    }

    post {
        always {
            cleanWs()
        }
    }
}