pipeline {
    agent any

    stages {
        stage('pull') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b68fb9c8-e776-4d50-969e-698d23512770', url: 'git@github.com:meditation-calm/order.git']]])
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '3046be44-6339-4e2a-bf68-bd67db94029a', path: '', url: 'http://192.168.211.138:8888/')], contextPath: '/', war: 'target/*.war'
            }
        }
    }
}
