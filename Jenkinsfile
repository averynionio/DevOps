def groovy
def py

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
                    if (fileExists('./pyJenkins.py')) {
                        echo 'found'
                    } else {
                        echo 'file not found'
                    }
                }
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GIthub', url: 'https://github.com/averynionio/DevOps.git']]])
            }
        }
        stage('git clone') {
            steps {
                git branch: 'main', credentialsId: 'GitHub', url: 'https://github.com/averynionio/DevOps.git'
              
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
                        //to: "${EMAIL_INFORM}"
                    )
                }
            }
        }
        stage("test") {
            steps { 
                echo "testing ..."
                script {
                    sh 'python ./pyJenkins.py'
                    cat 'README.md'
                }
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
