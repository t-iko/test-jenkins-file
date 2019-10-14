pipeline {
    agent any
    parameters {
        string(name: 'user', defaultValue: 'jenkins', description: 'コマンド')
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
            input "ユーザーを作成しても良いですか?"
        }    
        stage('ユーザーを作成する'){    
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
