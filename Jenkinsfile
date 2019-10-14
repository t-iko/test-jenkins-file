pipeline {
    agent any
    parameters {
        string(name: 'user', defaultValue: 'testuser', description: '作成したいユーザー名を入力してください')
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
                sh "./gradlew idCheck -Puser=${params.user}"
            } 
        }    
        stage('ユーザーを作成する'){
            input{
              message "ユーザーを作成しても良いですか?"
            }    
            steps {
                sh "./gradlew createUser -Puser=${params.user}"
            }
        }    
        stage('作成したUser IDが存在するか確認'){    
            steps {
                sh "./gradlew idCheck -Puser=${params.user}"
            }                    
        }
    }
}
//node {
//  echo 'My first Jenkinsfile'
//}
