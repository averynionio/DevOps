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
                        body: """<p>See "<a href="It is a test"</p>""",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']]
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
