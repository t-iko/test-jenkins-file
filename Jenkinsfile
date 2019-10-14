pipeline {
    agent any
    parameters {
        string(name: 'command', defaultValue: 'cat /etc/os-release', description: 'コマンド')
    }
    environment {
        reportDir = '/build/reports'
    }    
    stages {
        stage('hello') {
            steps {
                echo 'hello world'
                echo "${reportDir}"
            }
        }
        stage('cat'){    
            steps {
                sh "${params.command}"
                sh "./gradlew tasks"
            }    
        }
    }
}
//node {
//  echo 'My first Jenkinsfile'
//}
