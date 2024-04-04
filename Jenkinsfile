@Library('pipeline-library@master') _

pipeline {
    agent { label 'JAVA'}
    triggers {
        pollSCM('H/5 * * * 1-6')
    }
    stages {
        stage('Start mqtt broker')
        {
            steps {
             sh './start-broker.sh'
            }
        }
        stage('Build') {
            steps {
                withMaven(maven: 'Maven 3.8.1') {
                    sh 'mvn clean package'
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
