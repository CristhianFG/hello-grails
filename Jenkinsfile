#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git url: 'https://github.com/CristhianFG/hello-grails.git', branch: 'main' 
                
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
