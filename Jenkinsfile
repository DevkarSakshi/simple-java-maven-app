pipeline {
    agent any
    tools {
        jdk 'jdk17.0.2'    // EXACT name of your JDK in Jenkins
        maven 'maven'      // replace with the exact Maven name in Jenkins Global Tool Configuration
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                // Ensure deliver.bat exists or remove this step if not needed
                bat 'C:\\JenkinsProjects\\simple-java-maven-app\\jenkins\\scripts\\deliver.bat'
            }
        }
    }
}
