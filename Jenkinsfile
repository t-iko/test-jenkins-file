pipeline {
    agent any
    parameters {
        string(name: 'user', defaultValue: 'testuser', description: 'コマンド')
        string(name: 'server', defaultValue: 'webServer1', description: 'コマンド')
    }
    environment {
        reportDir = '/build/reports'
    }    
    stages {
        stage('hello') {
            steps {
                echo "${reportDir}"
            }
        }
        stage('指定したUser IDが存在するか確認'){    
            steps {
                sh "./gradlew idCheck -Puser=${params.user} -Pserver=${params.server}"
            } 
        }    
        stage('ユーザーを作成する'){
            input{
              message "ユーザーを作成しても良いですか?"
            }    
            steps {
                sh "./gradlew createUser -Puser=${params.user} -Pserver=${params.server}"
            }
        }    
        stage('作成したUser IDが存在するか確認'){    
            steps {
                sh "./gradlew idCheck -Puser=${params.user} -Pserver=${params.server}"
            }                    
        }
    }
}
//node {
//  echo 'My first Jenkinsfile'
//}
