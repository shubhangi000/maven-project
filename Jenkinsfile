

pipeline {
    agent any

    stages {
        stage('Maven Checkout') {
            steps {
                git 'https://github.com/shubhangi000/maven-project.git'
            }
        }
        stage('Maven Validate') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                // some block
                sh 'mvn validate'
                }
            }
        }
        stage('Maven Compile') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                // some block
                sh 'mvn compile'
                }
            }
        }
        stage('Package the code') {
            steps {
                withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                // some block
                sh 'mvn package'
                }
            }
        }
    }
}

