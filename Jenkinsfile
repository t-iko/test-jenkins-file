pipeline {
    agent any
    tools {
        gradle "GRADLE_LATEST"
    }
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
                sh "gradle -v"
            }    
        }
    }
}
//node {
//  echo 'My first Jenkinsfile'
//}
