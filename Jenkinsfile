pipeline {
    agent any

    //CI part

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
                sh 'mvn clean package'
                }
            }
        }

        //CD Part
        stage('deploy the code') {
            steps {
                sshagent(['DEVCICD']) {
                    sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.17.248:/usr/share/tomcat/webapps'
                }
            }
        }
    }
}


