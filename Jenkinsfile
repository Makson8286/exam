pipeline {
    agent any
    environment {
        TELEPUSH_TOKEN = '63b28a'
        ALERTMANAGER_YML_FILE = 'alertmanager.yml'
        ALERTMANAGER_YML_PATH = '/var/lib/jenkins/grafana/alertmanager.yml'
        ALERT_RULES_YML_FILE = 'alert.rules.yml'
        ALERT_RULES_YML_PATH = '/var/lib/jenkins/grafana/alert.rules.yml'
    }

    stages {
        stage('Clone') {
            steps {
                script {
                    
                    def alertmanagerFilePath = 'alertmanager.yml'
                    def content = readFile(file: alertmanagerFilePath)
                    content = content.replace('your-token', TELEPUSH_TOKEN)
                    writeFile(file: alertmanagerFilePath, text: content)

                    def dockerComposeFilePath = 'docker-compose.yml'
                    def dockerComposeContent = readFile(file: dockerComposeFilePath)
                    dockerComposeContent = dockerComposeContent.replace('/your/path/alertmanager.yml', ALERTMANAGER_YML_PATH)
                    dockerComposeContent = dockerComposeContent.replace('/your/path/alert.rules.yml', ALERT_RULES_YML_PATH)
                    writeFile(file: dockerComposeFilePath, text: dockerComposeContent)
                }
            }
        }
        stage('Build and Run') {
            steps {
                sh '''
                /var/lib/jenkins/grafana/docker-compose up -d
                '''
            }
        }
    }
}