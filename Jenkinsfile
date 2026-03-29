pipeline {
    agent any

    tools {
        maven 'M2_HOME'   // Must match exactly the Maven name in Jenkins Global Tool Config
        jdk 'JAVA_HOME'      // Add JDK tool too
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Sachin-dev-hub/my-irctc.git'
            }
        }

        stage('Build') {
            steps {
                // Optional: verify Maven version first
                sh 'mvn -v'
                
                // Build the project
                sh 'mvn clean package'
            }
        }

    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            echo 'Build Successful! WAR file generated in target folder.'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}
