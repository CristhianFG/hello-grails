#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withGradle {
                    sh './gradlew assemble'
                }
            }
        }
        stage('Test') {
            steps {
                withGradle {
                    sh './gradlew test'
                    configFileProvider([configFile(fileId: 'hello-grails-gradle.properties',
                                               targetLocation: 'gradle.properties')]) { 
                          sh './gradlew integrationTest'
                    }
                    withSonarQubeEnv(credentialsId: '47ed7d2fec72379227bb101747976923bf19f13e', installationName: 'local'){
                          sh './gradlew sonarqube'  
                    }
                }
            }
            post {
                always {
                    junit 'build/test-results/test/TEST-*.xml'
                }
            }
        }
    }
}
