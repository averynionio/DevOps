def groovy
pipeline {
    agent any
    stages {
        stage("init") {
            steps {
                script {
                    groovy = load "script.groovy"
                }
            }
        }
        stage("build") {
            steps {
                script {
                    groovy.buildApp()
                }
            }
        }
        stage("test") {
            steps { 
                echo "testing ...}"
            }
        }
        stage('Check style') {
            steps {
                echo "checking with..."
            }
        }
        stage('deploy') {
            steps { 
                echo "deploying with..."
             }
        }
    }
}
