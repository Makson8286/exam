pipeline {
    agent any
    environment {
        TELEPUSH_TOKEN = '63b28a'
        ALERTMANAGER_YML_FILE = 'alertmanager.yml'
        ALERTMANAGER_YML_PATH = '/home/ubuntu/monitoring/grafana/alertmanager.yml'
        ALERT_RULES_YML_FILE = 'alert.rules.yml'
        ALERT_RULES_YML_PATH = '/home/ubuntu/monitoring/grafana/alert.rules.yml'
    }

    stages {
        stage('Clone') {
            steps {
                script {
                        sh '''
                        cd /home/ubuntu/monitoring/
                        GIT_SSH_COMMAND="ssh -i $SSH_KEY" git clone git@github.com:Makson8286/grafana.git -b main
                        '''
                    
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
