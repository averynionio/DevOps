def groovy

pipeline {
    agent any
    environment {
            EMAIL_INFORM = 'averynionio@gmail.com; lniou@student.sfbu.edu'
    }
    stages {
        stage("init") {
            steps {
                script {
                    groovy = load "script.groovy"
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
                    emailext(
                        subject: "Build sucess in Jenkins",
                        body: 'test message',
                        recipientProviders: [developers(), requestor()],
                        to: "cy40923@gmail.com; niou19575@mail.npu.edu; ${EMAIL_INFORM}"
                    )
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
