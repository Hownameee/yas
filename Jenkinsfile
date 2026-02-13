pipeline {
    agent any

    stages {
        stage('Test Services') {
            parallel {
                stage('Backoffice BFF') {
                    when {
                        changeset "backoffice-bff/**"
                    }
                    steps {
                        dir('backoffice-bff') {
                            sh 'mvn test'
                        }
                    }
                }
            }
        }

        stage('Build Services') {
            parallel {
                stage('Backoffice BFF') {
                    when {
                        changeset "backoffice-bff/**"
                    }
                    steps {
                        dir('backoffice-bff') {
                            sh 'mvn package -DskipTests'
                        }
                    }
                }
            }
        }
    }
}