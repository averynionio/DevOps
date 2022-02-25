CODE_CHANGE = getGitChanges()
pipeline {
    agent any
    //環境變數 environment variables localhost:8080/env-var.html
    //在這裡設定可以套用到整個文件
    environment {
        NEW_VERSION = '1.3.0'
        SEVER_CREDENTIALS = credntials('credential-test') //在Jenkins裡面設定，輸入設定的ID
    }
    // only gradle, maven, jdk avalible others like yam, npm 要別的方式做
    tools {
        maven 'Maven' //need to pre install in Jenkins (Global Tool Configuration)
        gradle 'Gradle'
        jdk 'JavaJDK'
    }
    parameters {
        //string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choice: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        // 抓取專案
        stage('git clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/xgaryng/test_php.git'
            }  
            post {
                // git clone 失敗
                failure { echo "[*] git clone failure" }
                // git clone 成功
                success { echo '[*] git clone successful'}
            }
        }
        stage("build") {
            when {
                expression {
                    CODE_CHANGES == true && BRANCH_NAME  == "dev" || BRANCH_NAME  == "master"
                }
            }
            //only execute when code changed and current branch == dev or master
            steps {
                echo "building version ${NEW_VERSION}" //有引用，要double quote 否則會變string
                sh 'mvn install' // 因為Jenkins有在tools安裝好maven所以可以直接用
            }
        }
        stage("test") {
            when {
                expression {
                    params.executeTests == true //parameters設定的
                }
            }
            steps { echo "testing the app" }
        }
        stage('Check style') {
            // 執行 phpcs 並生成報告檔於 build/checkstyle.xml,
            // 副檔名為 php, 且檢查標準使用 PSR2 並忽略 autoload.php 以及 vendor
            // check style 的 pattern 使用剛剛產生出來的報告
            steps {}
        }
        //將檔案移到遠端主機
        stage('deploy') {
            steps { 
                echo "deploying with ${SEVER_CREDENTIALS}, ${params.VERSION}"
             }
        }
    
    }
}
