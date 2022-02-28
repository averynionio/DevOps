def groovy
def propsPath 
def props
def propsFile
pipeline {
    agent any
    stages {
        stage("init") {
            steps {
                script {
                    groovy = load "script.groovy"
                    propsPath = load "sample.properties"
                    //props = new Properties()
                    //propsFile = new File(propsPath)
                    //props.load(propsFile.newDataInputStream())
                }
            }
        }
        stage('git clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/averynionio/Practice'
              
            }  
            post {
                failure { echo "[*] git clone failure" }
                success { echo '[*] git clone successful'}
            }
        }
        stage("build") {
            steps {
                script {
                    groovy.buildApp()
                }
                echo props.getProperty("HW")
                echo props.getProperty("P1")
                echo props.getProperty("Custom")
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
