pipeline {
    agent any
    stages {
        stage("build") {
            steps {
                echo "building ..."
            }
        }
        stage("test") {
            steps { 
                echo "testing the app"
            }
        }
        stage('Check style') {
            steps {
                echo 'checking'
            }
        }
        stage('deploy') {
            steps { 
                echo "deploying with..."
             }
        }
    }
}
