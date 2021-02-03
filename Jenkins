#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                git url: 'https://github.com/CristhianFG/hello-grails.git' 
           }
        }
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
                    sh './gradlew -Dgeb.env=firefoxHedless iT'
                }
            }
        }
    }
}
