pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
            withMaven (
                maven: 'maven_3_5_0') {
                sh 'mvn clean compile'
            }
            }
        }
        stage('Test'){
            steps {
            withMaven (
                            maven: 'maven_3_5_0') {
                            sh 'mvn install -Dmaven.test.failure.ignore=true'
                        }
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('Deploy') {
            steps {
            withMaven (
                                        maven: 'maven_3_5_0') {
                sh 'mvn -Dmaven.skip.test=true deploy'
                }
            }
        }
    }
}