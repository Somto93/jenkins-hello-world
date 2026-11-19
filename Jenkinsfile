
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Clone the GitHub repository
                // git branch: 'main', url: 'https://github.com/Somto93/jenkins-hello-world'
                // Build the application without running tests
                sh 'mvn clean package -DskipTests=true'
            }
        }

        stage('Unit Test') {
            steps {
                // Execute unit tests
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // Publish the JUnit test results
            junit '**/target/surefire-reports/TEST-*.xml'
        }

        success {
            // Archive the generated JAR file
            archiveArtifacts artifacts: 'target/*.jar',
                             fingerprint: true
        }
    }
}
