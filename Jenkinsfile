@Library('pipeline-library@master') _

pipeline {
    agent { label 'JAVA'}
    triggers {
        pollSCM('H/5 * * * 1-6')
    }
    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'Maven 3.8.1') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
        stage('Deploy') {
            steps {
                withMaven(maven: 'Maven 3.8.1') {
                    sh 'mvn install'
                }
            }
        }
    }
}
