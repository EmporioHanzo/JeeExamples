pipeline {
    agent {
            label 'linux'
    }
    stages {
        stage ('compile/test') {
            steps {
                withMaven(globalMavenSettingsConfig: 'ae44f8b3-3bf7-4624-8e87-74659f3f817f', maven: 'maven393', mavenSettingsConfig: '', traceability: true) {
                    sh "mvn clean install"
                }
            }
        }
        stage('deploy to nexus') {
            steps {
                withMaven(globalMavenSettingsConfig: 'ae44f8b3-3bf7-4624-8e87-74659f3f817f', maven: 'maven393', mavenSettingsConfig: '', traceability: true) {
                     sh "mvn deploy -DskipTests"
                }
            }
        }
        stage('deploy to jboss') {
            steps {
                sh "echo deploying to jboss"
            }
        }
    }
}