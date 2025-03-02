pipeline {
    agent any

    //CI part

    stages {
        stage('SCM Checkout') {
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
                  sh 'mvn clean package'
                }
            }
        }

       stage('create docker image'){
            steps{
                sh 'docker build -t shubhangi000/del1:latest .'
            }
       }

       stage('push docker image to DockerHub'){
            steps{
                withDockerRegistry(credentialsId: 'docker_token', url: 'https://index.docker.io/v1/') 
                {
                    sh 'docker push shubhangi000/del1:latest'
                }
            }
       }
    }
}
