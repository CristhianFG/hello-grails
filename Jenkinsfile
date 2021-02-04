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
            post {
                 configFile: (fileId: 'hello-grails-gradle.properties',
                              variable: 'systemProp.geb.env')
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
