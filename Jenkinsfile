#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withGradle {
                    sh './gradlew assemble'
                }
                configFileProvider([configFile(fileId: 'hello-grails-gradle.properties', 
                                               targetLocation: 'systemProp.geb.env')]) {}
            }
        }
        stage('Test') {
            steps {
                withGradle {
                    sh './gradlew test'
                    sh './gradlew iT'
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
