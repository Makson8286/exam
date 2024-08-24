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
                    
                    def alertmanagerFile = new File('alertmanager.yml')
                    def content = alertmanagerFile.getText()
                    content = content.replace('your-token', TELEPUSH_TOKEN)
                    alertmanagerFile.setText(content)

                    def dockerComposeFile = new File('docker-compose.yml')
                    def dockerComposeContent = dockerComposeFile.getText()
                    dockerComposeContent = dockerComposeContent.replace('/your/path/alertmanager.yml', ALERTMANAGER_YML_PATH)
                    dockerComposeContent = dockerComposeContent.replace('/your/path/alert.rules.yml', ALERT_RULES_YML_PATH)
                    dockerComposeFile.setText(dockerComposeContent)
                }
            }
        }
        stage('Build and Run') {
            steps {
                sh '''
                docker-compose up -d
                '''
            }
        }
    }
}
