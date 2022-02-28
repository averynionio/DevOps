def groovy
pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choice: ['1.1.0', '1.2.0', '1.3.0'], description: '')
    }
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
                echo "testing version ${params.VERSION}"
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
