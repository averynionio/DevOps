CODE_CHANGE = getGitChanges()
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
            steps {}
        }
        stage('deploy') {
            steps { 
                echo "deploying with..."
             }
        }
    
    }
}
